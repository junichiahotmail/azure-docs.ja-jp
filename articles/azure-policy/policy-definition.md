---
title: Azure Policy 定義の構造 | Microsoft Docs
description: Azure Policy でリソース ポリシー定義を使用して、ポリシーが適用されるタイミングと実行されるアクションを示すことで、組織でのリソースの規則を確立する方法について説明します。
services: azure-policy
keywords: ''
author: bandersmsft
ms.author: banders
ms.date: 01/17/2018
ms.topic: article
ms.service: azure-policy
ms.custom: ''
ms.openlocfilehash: 42fdfa2eb629351c38fb72c20a62cd7d78acf229
ms.sourcegitcommit: 5b2ac9e6d8539c11ab0891b686b8afa12441a8f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="azure-policy-definition-structure"></a>Azure Policy の定義の構造

Azure Policy で使用されるリソース ポリシー定義を利用して、ポリシーが適用されるタイミングと実行されるアクションを示し、組織でのリソースの規則を確立することができます。 規則を定義することによって、コストを制御し、リソースをより簡単に管理することができます。 たとえば、特定の種類の仮想マシンのみを許可するように指定することができます。 また、すべてのリソースに特定のタグが指定されていることを必須にすることができます。 ポリシーは、すべての子リソースが継承します。 したがって、リソース グループに適用されたポリシーは、そのリソース グループのすべてのリソースに適用されます。

ポリシー定義を作成するには、JSON を使用します。 ポリシー定義には、以下のものに対する要素が含まれています。

* モード
* parameters
* 表示名
* 説明
* ポリシー規則
  * 論理評価
  * 効果

たとえば、次の JSON は、リソースがデプロイされる場所を制限するポリシーを示しています。

```json
{
  "properties": {
    "mode": "all",
    "parameters": {
      "allowedLocations": {
        "type": "array",
        "metadata": {
          "description": "The list of locations that can be specified when deploying resources",
          "strongType": "location",
          "displayName": "Allowed locations"
        }
      }
    },
    "displayName": "Allowed locations",
    "description": "This policy enables you to restrict the locations your organization can specify when deploying resources.",
    "policyRule": {
      "if": {
        "not": {
          "field": "location",
          "in": "[parameters('allowedLocations')]"
        }
      },
      "then": {
        "effect": "deny"
      }
    }
  }
}
```

すべての Azure Policy テンプレートのサンプルについては、「[Templates for Azure Policy (Azure Policy のテンプレート)](json-samples.md)」をご覧ください。

## <a name="mode"></a>Mode

**mode** では、ポリシーに対して評価されるリソースの種類を決定します。 サポートされているモードは次のとおりです。
* `all`: リソース グループとすべてのリソースの種類を評価します 
* `indexed`: タグと場所をサポートするリソースの種類のみを評価します

ほとんどの場合、**mode** は `all` に設定することをお勧めします。 ポータルを使用して作成されるポリシーの定義はすべて、`all` モードを使用します。 PowerShell または Azure CLI を使用する場合、**mode** パラメーターを手動で指定する必要があります。 ポリシー定義に **mode** の値が含まれていない場合は、下位互換性のために既定で `indexed` になります。

タグまたは場所を適用するポリシーを作成するときには、`indexed` を使用する必要があります。 これは必須ではありませんが、タグや場所をサポートしていないリソースが、コンプライアンス結果に非準拠として表れないようになります。 これの例外の 1 つは、**リソース グループ**です。 リソース グループに場所またはタグを適用しようとしているポリシーでは、**mode** を `all` に設定し、明確に `Microsoft.Resources/subscriptions/resourceGroup` 型をターゲットにする必要があります。 例については、[リソース グループのタグを適用する](scripts/enforce-tag-rg.md)ことに関する記事を参照してください。

## <a name="parameters"></a>parameters

パラメーターによって、ポリシー定義の数を減らし、ポリシーの管理を単純化できます。 1 つのフォームにあるフィールドのようなパラメーター `name`、`address``city``state` を考えてみてください。 これらのパラメーターは常に同じままですが、その値はフォームの個々の入力に基づいて変わります。 パラメーターは、ポリシーの作成時と同じように機能します。 ポリシー定義にパラメーターを含めることで、別の値を使用してさまざまなシナリオについてポリシーを再利用できます。

たとえば、リソースのデプロイ先の場所を制限するために、リソース プロパティのポリシーを定義できます。 この場合、ポリシーを作成するときに、次のパラメーターを宣言します。


```json
"parameters": {
  "allowedLocations": {
    "type": "array",
    "metadata": {
      "description": "The list of allowed locations for resources.",
      "displayName": "Allowed locations",
      "strongType": "location"
    }
  }
}
```

パラメーターの型は、文字列または配列のどちらも可能です。 メタデータ プロパティは、Azure Portal などのツールでわかりやすい情報を表示するために、使用されます。

メタデータ プロパティの中で **strongType** を使用して、Azure ポータル内にオプションの複数選択リストを用意できます。  現時点で **strongType** で使用できる値には、以下が含まれます。

* `"location"`
* `"resourceTypes"`
* `"storageSkus"`
* `"vmSKUs"`
* `"existingResourceGroups"`
* `"omsWorkspace"`

ポリシー規則では、次の構文でパラメーターを参照します。

```json
{
    "field": "location",
    "in": "[parameters('allowedLocations')]"
}
```

## <a name="display-name-and-description"></a>表示名と説明

ポリシー定義を識別し、定義が使用される際のコンテキストを指定するために、**displayName** と **description** を使用できます。

## <a name="policy-rule"></a>ポリシー規則

ポリシー規則は、**If** と **Then** ブロックで構成されています。 **If** ブロックでは、いつポリシーが適用されるかを指定する、1 つ以上の条件を定義します。 これらの条件に論理演算子を適用して、ポリシーのシナリオを細かく定義することができます。

**Then** ブロックでは、**If** 条件が満たされる場合に生じる効果を定義します。

```json
{
  "if": {
    <condition> | <logical operator>
  },
  "then": {
    "effect": "deny | audit | append | auditIfNotExists | deployIfNotExists"
  }
}
```

### <a name="logical-operators"></a>論理演算子

サポートされている論理演算子は、次のとおりです。

* `"not": {condition  or operator}`
* `"allOf": [{condition or operator},{condition or operator}]`
* `"anyOf": [{condition or operator},{condition or operator}]`

**not** 構文は、条件の結果を反転します。 **allOf** 構文 (**And** 論理演算に似ています) では、すべての条件が真である必要があります。 **anyOf** 構文 (**Or** 論理演算に似ています) では、1 つ以上の条件が真である必要があります。

論理演算子は、入れ子にすることができます。 次の例は、**allOf** 演算内で入れ子になっている **not** 演算を示しています。

```json
"if": {
  "allOf": [
    {
      "not": {
        "field": "tags",
        "containsKey": "application"
      }
    },
    {
      "field": "type",
      "equals": "Microsoft.Storage/storageAccounts"
    }
  ]
},
```

### <a name="conditions"></a>条件

条件は、**フィールド**が特定の基準を満たすかどうかを評価します。 サポートされている条件は次のとおりです。

* `"equals": "value"`
* `"notEquals": "value"`
* `"like": "value"`
* `"notLike": "value"`
* `"match": "value"`
* `"notMatch": "value"`
* `"contains": "value"`
* `"notContains": "value"`
* `"in": ["value1","value2"]`
* `"notIn": ["value1","value2"]`
* `"containsKey": "keyName"`
* `"notContainsKey": "keyName"`
* `"exists": "bool"`

**like** 条件や **notLike** 条件を使用する場合は、値の中でワイルドカード (*) を指定できます。

**match** 条件や **notMatch** 条件を使うときは、任意の数字を表す `#` や任意の文字を表す `?` のほか、具体的な文字を指定することができます。 [承認されている VM イメージ](scripts/allowed-custom-images.md)に関する記事で、例を確認してください。

### <a name="fields"></a>フィールド
条件は、フィールドを使用して構成されます。 フィールドは、リソースの状態の記述に使用されるリソース要求ペイロード内のプロパティを表します。  

次のフィールドがサポートされています。

* `name`
* `fullName`
  * 親を含むリソースの完全な名前 (例:"myServer/myDatabase") を返します
* `kind`
* `type`
* `location`
* `tags`
* `tags.tagName`
* `tags[tagName]`
  * このかっこ構文は、ピリオドを含むタグ名をサポートしています
* プロパティのエイリアス: 一覧については、「[エイリアス](#aliases)」を参照してください。

### <a name="alternative-accessors"></a>代替アクセサー
**Field** は、ポリシー規則で使用されるプライマリ アクセサーです。 これは、評価対象となっているリソースを直接検査します。 ただし、ポリシーは他のアクセサー **source** をサポートしています。

```json
"source": "action",
"equals": "Microsoft.Compute/virtualMachines/write"
```

**source** がサポートしている値は **action** の 1 つだけです。 action は、評価対象となっている要求の承認アクションを返します。 承認アクションは、[アクティビティ ログ](../monitoring-and-diagnostics/monitoring-activity-log-schema.md)の承認セクションで公開されています。

ポリシーがバック グラウンドで既存のリソースを評価するときには、そのリソースの種類に対する **action** を `/write` 承認アクションに設定します。

### <a name="effect"></a>効果
ポリシーでは、次の種類の効果がサポートされています。

* **deny** は監査ログでイベントを生成し、要求は失敗します。
* **audit** は監査ログで警告イベントを生成しますが、要求は失敗しません。
* **append** は定義済みのフィールド セットを要求に追加します。
* **AuditIfNotExists** は、リソースが存在しない場合に監査を有効にします。
* **DeployIfNotExists** は、リソースが存在しない場合にリソースをデプロイします。 現在この効果は、組み込みポリシーを通じてのみサポートされます。

**append** の場合、次のように詳細を指定する必要があります。

```json
"effect": "append",
"details": [
  {
    "field": "field name",
    "value": "value of the field"
  }
]
```

値には文字列または JSON 形式オブジェクトを指定できます。

**AuditIfNotExists** および **DeployIfNotExists** を使用すると、関連するリソースの存在を評価したうえで、そのリソースが存在しない場合に、ルールと該当する効果を適用することができます。 たとえば、すべての仮想ネットワークを対象に Network Watcher のデプロイを要求することができます。
仮想マシン拡張機能がデプロイされていない場合の監査の例については、[拡張機能が存在しない場合の監査](scripts/audit-ext-not-exist.md)に関するページを参照してください。


## <a name="aliases"></a>エイリアス

リソースの種類に固有のプロパティにアクセスするには、プロパティのエイリアスを使用します。 エイリアスを使用すると、リソースのプロパティに使用できる値または条件を制限できます。 各エイリアスは、特定のリソースの種類について異なる API バージョンのパスにマップされます。 ポリシーの評価時に、ポリシー エンジンはその API バージョンのプロパティ パスを取得します。

**Microsoft.Cache/Redis**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Cache/Redis/enableNonSslPort | 非 ssl Redis サーバー ポート (6379) が有効かどうかを設定します。 |
| Microsoft.Cache/Redis/shardCount | Premium クラスター キャッシュに作成するシャードの数を設定します。  |
| Microsoft.Cache/Redis/sku.capacity | デプロイする Redis キャッシュのサイズを設定します。  |
| Microsoft.Cache/Redis/sku.family | 使用する SKU ファミリを設定します。 |
| Microsoft.Cache/Redis/sku.name | デプロイする Redis キャッシュの種類を設定します。 |

**Microsoft.Cdn/profiles**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.CDN/profiles/sku.name | 価格レベルの名前を設定します。 |

**Microsoft.Compute/disks**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Compute/imageOffer | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージを設定します。 |
| Microsoft.Compute/imagePublisher | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの発行元を設定します。 |
| Microsoft.Compute/imageSku | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの SKU を設定します。 |
| Microsoft.Compute/imageVersion | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージのバージョンを設定します。 |


**Microsoft.Compute/virtualMachines**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Compute/imageId | 仮想マシンの作成に使用されるイメージの識別子を設定します。 |
| Microsoft.Compute/imageOffer | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージを設定します。 |
| Microsoft.Compute/imagePublisher | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの発行元を設定します。 |
| Microsoft.Compute/imageSku | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの SKU を設定します。 |
| Microsoft.Compute/imageVersion | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージのバージョンを設定します。 |
| Microsoft.Compute/licenseType | イメージまたはディスクがオンプレミスでライセンスされることを設定します。 この値は、Windows Server オペレーティング システムを含むイメージでのみ使用されます。  |
| Microsoft.Compute/virtualMachines/imageOffer | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージを設定します。 |
| Microsoft.Compute/virtualMachines/imagePublisher | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの発行元を設定します。 |
| Microsoft.Compute/virtualMachines/imageSku | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの SKU を設定します。 |
| Microsoft.Compute/virtualMachines/imageVersion | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージのバージョンを設定します。 |
| Microsoft.Compute/virtualMachines/osDisk.Uri | Vhd URI を設定します。 |
| Microsoft.Compute/virtualMachines/sku.name | 仮想マシンのサイズを設定します。 |
| Microsoft.Compute/virtualMachines/availabilitySet.id | 仮想マシンで使用する可用性セット ID を設定します。 |

**Microsoft.Compute/virtualMachines/extensions**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Compute/virtualMachines/extensions/publisher | 拡張機能の発行元の名前を設定します。 |
| Microsoft.Compute/virtualMachines/extensions/type | 拡張機能の種類を設定します。 |
| Microsoft.Compute/virtualMachines/extensions/typeHandlerVersion | 拡張機能のバージョンを設定します。 |

**Microsoft.Compute/virtualMachineScaleSets**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Compute/imageId | 仮想マシンの作成に使用されるイメージの識別子を設定します。 |
| Microsoft.Compute/imageOffer | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージを設定します。 |
| Microsoft.Compute/imagePublisher | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの発行元を設定します。 |
| Microsoft.Compute/imageSku | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージの SKU を設定します。 |
| Microsoft.Compute/imageVersion | 仮想マシンを作成するために使用されるプラットフォーム イメージまたはマーケットプレース イメージのバージョンを設定します。 |
| Microsoft.Compute/licenseType | イメージまたはディスクがオンプレミスでライセンスされることを設定します。 この値は、Windows Server オペレーティング システムを含むイメージでのみ使用されます。 |
| Microsoft.Compute/VirtualMachineScaleSets/computerNamePrefix | スケール セット内のすべての仮想マシンのコンピューター名プレフィックスを設定します。 |
| Microsoft.Compute/VirtualMachineScaleSets/osdisk.imageUrl | ユーザー イメージの BLOB URI を設定します。 |
| Microsoft.Compute/VirtualMachineScaleSets/osdisk.vhdContainers | スケール セットのオペレーティング システム ディスクを保存するために使用されるコンテナーの URI を設定します。 |
| Microsoft.Compute/VirtualMachineScaleSets/sku.name | スケール セット内の仮想マシンのサイズを設定します。 |
| Microsoft.Compute/VirtualMachineScaleSets/sku.tier | スケール セット内の仮想マシンのレベルを設定します。 |

**Microsoft.Network/applicationGateways**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Network/applicationGateways/sku.name | ゲートウェイのサイズを設定します。 |

**Microsoft.Network/virtualNetworkGateways**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Network/virtualNetworkGateways/gatewayType | この仮想ネットワーク ゲートウェイの種類を設定します。 |
| Microsoft.Network/virtualNetworkGateways/sku.name | ゲートウェイの SKU 名を設定します。 |

**Microsoft.Sql/servers**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Sql/servers/version | サーバーのバージョンを設定します。 |

**Microsoft.Sql/databases**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Sql/servers/databases/edition | データベースのエディションを設定します。 |
| Microsoft.Sql/servers/databases/elasticPoolName | データベースが所属するエラスティック プールの名前を設定します。 |
| Microsoft.Sql/servers/databases/requestedServiceObjectiveId | データベースの構成済みのサービス レベルの目標 ID を設定します。 |
| Microsoft.Sql/servers/databases/requestedServiceObjectiveName | データベースの構成済みのサービス レベルの目標の名前を設定します。  |

**Microsoft.Sql/elasticpools**

| エイリアス | [説明] |
| ----- | ----------- |
| servers/elasticpools | Microsoft.Sql/servers/elasticPools/dtu | データベースのエラスティック プールの共有 DTU の合計を設定します。 |
| servers/elasticpools | Microsoft.Sql/servers/elasticPools/edition | エラスティック プールのエディションを設定します。 |

**Microsoft.Storage/storageAccounts**

| エイリアス | [説明] |
| ----- | ----------- |
| Microsoft.Storage/storageAccounts/accessTier | 課金のために使用されるアクセス レベルを設定します。 |
| Microsoft.Storage/storageAccounts/accountType | SKU 名を設定します。 |
| Microsoft.Storage/storageAccounts/enableBlobEncryption | BLOB ストレージ サービスに格納されるときに、サービスがデータを暗号化するかどうかを設定します。 |
| Microsoft.Storage/storageAccounts/enableFileEncryption | ファイル ストレージ サービスに格納されるときに、サービスがデータを暗号化するかどうかを設定します。 |
| Microsoft.Storage/storageAccounts/sku.name | SKU 名を設定します。 |
| Microsoft.Storage/storageAccounts/supportsHttpsTrafficOnly | ストレージ サービスへの https トラフィックのみを許可するように設定します。 |
| Microsoft.Storage/storageAccounts/networkAcls.virtualNetworkRules[*].id | Virtual Network サービス エンドポイントが有効にされているかどうかを確認します。 |

## <a name="initiatives"></a>イニシアティブ

イニシアティブを使用すると、複数の関連するポリシー定義をグループ化できます。グループを単一の項目として操作するので、割り当てと管理が単純になります。 たとえば、関連するすべてのタグ付けポリシー定義を 1 つのイニシアティブとしてグループ化できます。 それぞれのポリシーを個別に割り当てるのではなく、イニシアティブを適用することになります。

次の例は、2 つのタグ (`costCenter` および `productName`) を扱うためのイニシアティブの作成方法を示しています。 2 つの組み込みポリシーを使用して、既定のタグの値を適用しています。


```json
{
    "properties": {
        "displayName": "Billing Tags Policy",
        "policyType": "Custom",
        "description": "Specify cost Center tag and product name tag",
        "parameters": {
            "costCenterValue": {
                "type": "String",
                "metadata": {
                    "description": "required value for Cost Center tag"
                }
            },
            "productNameValue": {
                "type": "String",
                "metadata": {
                    "description": "required value for product Name tag"
                }
            }
        },
        "policyDefinitions": [
            {
                "policyDefinitionId": "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
                "parameters": {
                    "tagName": {
                        "value": "costCenter"
                    },
                    "tagValue": {
                        "value": "[parameters('costCenterValue')]"
                    }
                }
            },
            {
                "policyDefinitionId": "/providers/Microsoft.Authorization/policyDefinitions/2a0e14a6-b0a6-4fab-991a-187a4f81c498",
                "parameters": {
                    "tagName": {
                        "value": "costCenter"
                    },
                    "tagValue": {
                        "value": "[parameters('costCenterValue')]"
                    }
                }
            },
            {
                "policyDefinitionId": "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
                "parameters": {
                    "tagName": {
                        "value": "productName"
                    },
                    "tagValue": {
                        "value": "[parameters('productNameValue')]"
                    }
                }
            },
            {
                "policyDefinitionId": "/providers/Microsoft.Authorization/policyDefinitions/2a0e14a6-b0a6-4fab-991a-187a4f81c498",
                "parameters": {
                    "tagName": {
                        "value": "productName"
                    },
                    "tagValue": {
                        "value": "[parameters('productNameValue')]"
                    }
                }
            }
        ]
    },
    "id": "/subscriptions/<subscription-id>/providers/Microsoft.Authorization/policySetDefinitions/billingTagsPolicy",
    "type": "Microsoft.Authorization/policySetDefinitions",
    "name": "billingTagsPolicy"
}
```

## <a name="next-steps"></a>次の手順

- 「[Templates for Azure Policy (Azure Policy のテンプレート)](json-samples.md)」で、Azure Policy テンプレートのサンプルを確認する
