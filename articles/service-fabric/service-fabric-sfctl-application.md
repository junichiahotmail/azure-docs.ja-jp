---
title: Azure Service Fabric CLI- sfctl application | Microsoft Docs
description: Service Fabric CLI- sfctl application のコマンドについて説明します。
services: service-fabric
documentationcenter: na
author: rwike77
manager: timlt
editor: ''
ms.assetid: ''
ms.service: service-fabric
ms.devlang: cli
ms.topic: reference
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 02/23/2018
ms.author: ryanwi
ms.openlocfilehash: fe0ef5c81b1ef6bef298e65cde3649c9464089d8
ms.sourcegitcommit: 5b2ac9e6d8539c11ab0891b686b8afa12441a8f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="sfctl-application"></a>sfctl application
アプリケーションおよびアプリケーションの種類を作成、削除、および管理します。

## <a name="commands"></a>コマンド

|コマンド|[説明]|
| --- | --- |
| create       | 指定された説明を使用して、Service Fabric アプリケーションを作成します。|
| 削除       | 既存の Service Fabric アプリケーションを削除します。|
| deployed     | Service Fabric ノードにデプロイされたアプリケーションに関する情報を取得します。|
| deployed-health | Service Fabric ノードにデプロイされたアプリケーションの正常性に関する情報を取得します。|
| deployed-list| Service Fabric ノードにデプロイされたアプリケーションの一覧を取得します。|
| health       | Service Fabric アプリケーションの正常性を取得します。|
| info         | Service Fabric アプリケーションの情報を取得します。|
| list         | パラメーターとして指定されたフィルターに一致する Service Fabric クラスターで作成されたアプリケーションの一覧を取得します。|
| load | Service Fabric アプリケーションの負荷情報を取得します。 |
| manifest     | アプリケーションの種類を記述するマニフェストを取得します。|
| provision    | 外部ストアの .sfpkg パッケージまたはイメージ ストアのアプリケーション パッケージを使って、Service Fabric アプリケーションの種類をプロビジョニングするか、クラスターに登録します。|
| report-health| Service Fabric アプリケーションの正常性レポートを送信します。|
| 型         | 指定した名前と完全に一致する Service Fabric クラスター内のアプリケーションの種類の一覧を取得します。|
| type-list    | Service Fabric クラスター内のアプリケーションの種類の一覧を取得します。|
| unprovision  | Service Fabric アプリケーションの種類をクラスターから削除または登録解除します。|
| upgrade      | Service Fabric クラスターで、アプリケーションのアップグレードを開始します。|
| upgrade-resume  | Service Fabric クラスターで、アプリケーションのアップグレードを再開します。|
| upgrade-rollback| Service Fabric クラスター内で現在進行中のアプリケーションのアップグレードのロールバックを開始します。|
| upgrade-status  | このアプリケーションで実行された最新のアップグレードの詳細を取得します。|
| upload       | Service Fabric アプリケーション パッケージをイメージ ストアにコピーします。|

## <a name="sfctl-application-create"></a>sfctl application create
指定された説明を使用して、Service Fabric アプリケーションを作成します。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --app-name    [必須]| 'fabric:' URI スキームを含むアプリケーションの名前。|
| --app-type    [必須]| アプリケーション マニフェストで検出されたアプリケーションの種類名。|
| --app-version [必須]| アプリケーション マニフェストで定義されているアプリケーションの種類のバージョン。|
| --max-node-count     | Service Fabric がこのアプリケーション用に容量を予約するノードの最大数。 このアプリケーションのサービスがこれらすべてのノードに配置されるわけではありません。|
| --metrics            | アプリケーションの容量のメトリックの説明の JSON でエンコードされた一覧。 メトリックは名前として定義され、アプリケーションが存在する各ノードの一連の容量に関連付けられます。|
| --min-node-count     | Service Fabric がこのアプリケーション用に容量を予約するノードの最小数。 このアプリケーションのサービスがこれらすべてのノードに配置されるわけではありません。|
| --parameters         | アプリケーションの作成時に適用される、アプリケーション パラメーター オーバーライドの JSON でエンコードされた一覧。|
| --timeout -t         | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug              | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h            | このヘルプ メッセージを表示して終了します。|
| --output -o          | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query              | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose            | ログ記録の詳細度を上げます。 完全なデバッグ ログには --debug を使用します。|

## <a name="sfctl-application-delete"></a>sfctl application delete
既存の Service Fabric アプリケーションを削除します。

既存の Service Fabric アプリケーションを削除します。 アプリケーションを削除するには、その前にアプリケーションが作成されている必要があります。 アプリケーションを削除すると、そのアプリケーションの一部となっているすべてのサービスが削除されます。 既定では Service Fabric は、安全な方法でサービスのレプリカを閉じてからサービスを削除しようとします。 ただし、サービスにレプリカを正常に終了できない問題がある場合は、削除操作に時間がかかったり、スタックする場合があります。 正常に閉じるシーケンスをスキップし、アプリケーションとそのすべてのサービスを強制的に削除するには、省略可能な ForceRemove フラグを使用します。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-id [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は "~" 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。|
| --force-remove          | 正常なシャットダウン シーケンスを経由せずに、Service Fabric アプリケーションまたはサービスを強制的に削除します。 このパラメーターを使用して、レプリカの正常な終了を妨げるサービス コードでの問題により、削除がタイムアウトしたアプリケーションまたはサービスを強制的に削除することができます。|
| --timeout -t            | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                 | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h               | このヘルプ メッセージを表示して終了します。|
| --output -o             | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query                 | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose               | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-deployed"></a>sfctl application deployed
Service Fabric ノードにデプロイされたアプリケーションに関する情報を取得します。

Service Fabric ノードにデプロイされたアプリケーションに関する情報を取得します。  指定されたアプリケーション ID がシステム アプリケーションのものである場合、このクエリはシステム アプリケーションの情報を返します。 結果には、アクティブ、アクティブ化中、およびダウンロード中の状態の展開済みアプリケーションが含まれます。 このクエリでは、ノード名がクラスター上のノードに対応している必要があります。 指定されたノード名がクラスター上のアクティブな Service Fabric ノードを示していない場合、クエリは失敗します。
     
### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-id [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は "~" 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。|
| --node-name    [必須]| ノード名。|
| --timeout -t            | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                 | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h               | このヘルプ メッセージを表示して終了します。|
| --output -o             | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query                 | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose               | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-health"></a>sfctl application health
Service Fabric アプリケーションの正常性を取得します。

Service Fabric アプリケーションの正常性の状態を返します。 応答で、Ok、Error、Warning のいずれかの正常性の状態が報告されます。 正常性ストアにエンティティが見つからない場合は、Error が返されます。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-id                 [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は "~" 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。|
| --deployed-applications-health-state-filter| 正常性の状態に基づくアプリケーションの正常性クエリの結果で返されるデプロイされたアプリケーションの正常性の状態オブジェクトをフィルター処理できます。 このパラメーターに指定できる値には、次の正常性の状態のいずれかの整数値が含まれます。 フィルターに一致するデプロイ済みアプリケーションのみが返されます。 すべてのデプロイ済みアプリケーションは、集計された正常性の状態を評価するために使用されます。 指定しない場合、すべてのエントリが返されます。 状態値はフラグベースの列挙型であるため、値はビット演算子 'OR' を使用して取得したこれらの値の組み合わせが可能です。 たとえば、指定した値が 6 の場合、HealthState の値が OK (2) と Warning (4) のデプロイ済みアプリケーションの正常性の状態が返されます。 - Default - 既定値。 任意の HealthState と一致します。 値は 0 です。 - None - どの HealthState 値とも一致しないフィルター。 状態の特定のコレクションの結果が返されないようにするために使用されます。 値は 1 です。 - Ok - HealthState 値が Ok の入力に一致するフィルター。 値は 2 です。 - Warning - HealthState 値が Warning の入力に一致するフィルター。 値は 4 です。 - Error - HealthState 値が Error の入力に一致するフィルター。 値は 8 です。 - All - 任意の HealthState 値の入力に一致するフィルター。 値は 65535 です。|
| --events-health-state-filter            | 正常性の状態に基づいて返された HealthEvent オブジェクトのコレクションをフィルター処理できます。 このパラメーターに指定できる値には、次の正常性の状態のいずれかの整数値が含まれます。 フィルターに一致するイベントのみが返されます。 すべてのイベントが集計された正常性の状態を評価するために使用されます。 指定しない場合、すべてのエントリが返されます。 状態値はフラグベースの列挙型であるため、値はビット演算子 'OR' を使用して取得したこれらの値の組み合わせが可能です。 たとえば、指定した値が 6 の場合、HealthState の値が OK (2) と Warning (4) のすべてのイベントが返されます。 - Default - 既定値。 任意の HealthState と一致します。 値は 0 です。 - None - どの HealthState 値とも一致しないフィルター。 状態の特定のコレクションの結果が返されないようにするために使用されます。 値は 1 です。 - Ok - HealthState 値が Ok の入力に一致するフィルター。 値は 2 です。 - Warning - HealthState 値が Warning の入力に一致するフィルター。 値は 4 です。 - Error - HealthState 値が Error の入力に一致するフィルター。 値は 8 です。 - All - 任意の HealthState 値の入力に一致するフィルター。 値は 65535 です。|
| --exclude-health-statistics | 正常性の統計情報がクエリ結果の一部として返されるかどうかを示します。 既定では false です。 統計情報は、正常性の状態が Ok、Warning、および Error の子エンティティの数を示します。|
| --services-health-state-filter          | 正常性状態に基づくサービス正常性クエリの結果で返される、サービスの正常性状態のオブジェクトのフィルター処理ができます。 このパラメーターに指定できる値には、次の正常性の状態のいずれかの整数値が含まれます。 フィルターに一致するサービスのみが返されます。 すべてのサービスが集計された正常性の状態を評価するために使用されます。 指定しない場合、すべてのエントリが返されます。 状態値はフラグベースの列挙型であるため、値はビット演算子 'OR' を使用して取得したこれらの値の組み合わせが可能です。 たとえば、指定した値が 6 の場合、HealthState の値が OK (2) と Warning (4) のサービスの正常性の状態が返されます。 - Default - 既定値。 任意の HealthState と一致します。 値は 0 です。 - None - どの HealthState 値とも一致しないフィルター。 状態の特定のコレクションの結果が返されないようにするために使用されます。 値は 1 です。 - Ok - HealthState 値が Ok の入力に一致するフィルター。 値は 2 です。 - Warning - HealthState 値が Warning の入力に一致するフィルター。 値は 4 です。 - Error - HealthState 値が Error の入力に一致するフィルター。 値は 8 です。 - All - 任意の HealthState 値の入力に一致するフィルター。 値は 65535 です。|
| --timeout -t                            | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                                 | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                               | このヘルプ メッセージを表示して終了します。|
| --output -o                             | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query                                 | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose                               | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-info"></a>sfctl application info
Service Fabric アプリケーションの情報を取得します。

Service Fabric クラスターで作成された、または作成中の、パラメーターとして指定されているものと同じ名前のアプリケーションの情報を返します。 応答には、名前、種類、状態、パラメーター、およびアプリケーションに関するその他の詳細が含まれています。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-id      [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は "~" 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。|
| --exclude-application-parameters| アプリケーションのパラメーターを結果から除外するかどうかを指定するフラグ。|
| --timeout -t                 | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                      | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                    | このヘルプ メッセージを表示して終了します。|
| --output -o                  | 出力形式。  使用できる値は、json、jsonc、table、tsv です。             既定値は json です。|
| --query                      | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose                    | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-list"></a>sfctl application list
パラメーターとして指定されたフィルターに一致する Service Fabric クラスターで作成されたアプリケーションの一覧を取得します。

Service Fabric クラスターで作成された、または作成中の、パラメーターとして指定されているフィルターに一致するアプリケーションの情報を返します。 応答には、名前、種類、状態、パラメーター、およびアプリケーションに関するその他の詳細が含まれています。 アプリケーションが 1 ページに収まらない場合、1 ページの結果と継続トークンが返されます。これは次のページを取得するために使用できます。 フィルター ApplicationTypeName と ApplicationDefinitionKindFilter を同時に指定することはできません。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
|--application-definition-kind-filter| Service Fabric アプリケーションを定義するためのメカニズムである ApplicationDefinitionKind でのフィルターに使われます。 - Default - 既定値。"All" を選んだ場合と同じ機能を実行します。 値は 0 です。 - All - ApplicationDefinitionKind 値の入力と一致するフィルター。 値は 65535 です。 - ServiceFabricApplicationDescription - ApplicationDefinitionKind 値 ServiceFabricApplicationDescription の入力と一致するフィルター。 値は 1 です。 - Compose - ApplicationDefinitionKind 値 Compose の入力と一致するフィルター。 値は 2 です。|
| --application-type-name      | クエリを実行するアプリケーションをフィルター処理するために使用されるアプリケーションの種類名。 この値にアプリケーションの種類のバージョンを含めることはできません。|
| --continuation-token         | 継続トークンのパラメーターは、次の結果セットを取得するために使用されます。 システムからの結果が 1 つの応答に収まらないときに、空以外の値を持つ継続トークンが API の応答に含まれます。 この値が次の API 呼び出しに渡されると、API が次の結果セットを返します。 それ以上の結果がない場合は、継続トークンに値が含まれません。 このパラメーターの値を URL にエンコードすることはできません。|
| --exclude-application-parameters| アプリケーションのパラメーターを結果から除外するかどうかを指定するフラグ。|
| --max-results|ページング クエリの一部として返される結果の最大数。 このパラメーターは、返される結果の数に上限を定義します。 返された結果が、構成で定義したメッセージの最大サイズの制限に収まらない場合は、指定した最大結果数よりも少なくなる場合があります。 このパラメーターがゼロまたは指定されていない場合、ページング クエリには、応答メッセージに収まるできるだけ多くの結果が含まれます。|
| --timeout -t                 | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                      | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                    | このヘルプ メッセージを表示して終了します。|
| --output -o                  | 出力形式。  使用できる値は、json、jsonc、table、tsv です。             既定値は json です。|
| --query                      | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose                    | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-load"></a>sfctl application load
Service Fabric アプリケーションの負荷情報を取得します。

Service Fabric クラスターで作成された、または作成中の、パラメーターとして指定されているものと同じ名前のアプリケーションの負荷情報を返します。 応答には、名前、最小ノード数、最大ノード数、アプリが現在使用しているノードの数、およびアプリケーションの負荷メトリック情報が含まれます。

### <a name="arguments"></a>引数
|引数|[説明]|
| --- | --- |
|--application-id [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は "~" 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。 |
| --timeout -t               | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数
|引数|[説明]|
| --- | --- |
|--debug                    | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
    --help -h                  | このヘルプ メッセージを表示して終了します。|
    --output -o                | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
    --query                    | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
    --verbose                  | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-manifest"></a>sfctl application manifest
アプリケーションの種類を記述するマニフェストを取得します。
        
アプリケーションの種類を記述するマニフェストを取得します。 応答には、アプリケーション マニフェスト XML が文字列として含まれています。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-type-name    [必須]| アプリケーションの種類名。|
| --application-type-version [必須]| アプリケーションの種類のバージョン。|
| --timeout -t                      | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                           | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                         | このヘルプ メッセージを表示して終了します。|
| --output -o                       | 出力形式。  使用できる値は、json、jsonc、table、tsv です。                  既定値は json です。|
| --query                           | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose                         | ログ記録の詳細度を上げます。 完全なデバッグ ログには --debug を使用します。|

## <a name="sfctl-application-provision"></a>sfctl application provision
外部ストアの SFPKG パッケージまたはイメージ ストアのアプリケーション パッケージを使って、Service Fabric アプリケーションの種類をプロビジョニングするか、クラスターに登録します。

Service Fabric アプリケーションの種類をクラスターにプロビジョニングします。 すべての新しいアプリケーションをインスタンス化するには、これが必要です。 プロビジョニング操作は、relativePathInImageStore で指定されているアプリケーション パッケージで、または外部 SFPKG の URI を使って、実行することができます。 --external-provision が設定されていない場合、このコマンドはイメージ ストアからアプリケーション パッケージをプロビジョニングします。
        


### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-package-download-uri| HTTP または HTTPS プロトコルを使ってアプリケーション パッケージをダウンロードできる ".sfpkg" アプリケーション パッケージのパスです。 外部ストアからのプロビジョニングの場合だけです。 アプリケーション パッケージは、ファイルをダウンロードするための GET 操作を提供する外部ストアに格納できます。 サポートされているプロトコルは HTTP と HTTPS であり、パスは READ アクセスを許可する必要があります。|
| --application-type-build-path       | プロビジョニングの種類のイメージ ストアの場合だけです。 以前のアップロード操作の間に指定されたイメージ ストアのアプリケーション パッケージに対する相対パスです。 |
| --application-type-name| 外部ストアからのプロビジョニングの場合だけです。 アプリケーションの種類の名前は、アプリケーション マニフェストで検出されたアプリケーションの種類の名前を表します。|
| --application-type-version| 外部ストアからのプロビジョニングの場合だけです。 アプリケーションの種類のバージョンは、アプリケーション マニフェストで検出されたアプリケーションの種類のバージョンを表します。|
| --external-provision| アプリケーション パッケージを登録またはプロビジョニングできる場所です。 以前に外部ストアにアップロードされたアプリケーション パッケージに対するプロビジョニングであることを示します。 アプリケーション パッケージの拡張子は *.sfpkg です。|
| --no-wait| プロビジョニングを非同期に実行する必要があるかどうかを示します。  true に設定すると、システムによって要求が受け付けられるとプロビジョニング操作は戻り、タイムアウト制限なしに続行されます。 既定値は false です。 大規模なアプリケーション パッケージの場合、値を true に設定することをお勧めします。|
| --timeout -t                      | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                              | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                            | このヘルプ メッセージを表示して終了します。|
| --output -o                          | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query                              | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose                            | ログ記録の詳細度を上げます。 完全なデバッグ ログには --debug を使用します。|

## <a name="sfctl-application-type"></a>sfctl application type

指定した名前と完全に一致する Service Fabric クラスター内のアプリケーションの種類の一覧を取得します。

Service Fabric クラスターでプロビジョニングされた、またはプロビジョニング中のアプリケーションの種類に関する情報を返します。 これらは、名前がパラメーターとして指定されたものと完全に一致し、指定されたクエリ パラメーターに適合するアプリケーションの種類の結果です。 アプリケーションの種類の名前に一致するアプリケーションの種類のすべてのバージョンが返されます。各バージョンは 1 つのアプリケーションの種類として返されます。 応答には、名前、バージョン、状態、およびアプリケーションの種類に関するその他の詳細が含まれています。 これがページング クエリです。つまり、すべてのアプリケーションの種類が 1 ページに収まらない場合、1 ページの結果と次のページを取得するために使用できる継続トークンが返されます。 たとえば、10 個のアプリケーションの種類があって、1 ページに最初の 3 つのアプリケーションの種類しか収まらない場合、または max results が 3 に設定されている場合は、3 が返されます。 残りの結果にアクセスするには、返された継続トークンを次のクエリで使用して、後続のページを取得します。 後続のページが存在しない場合は、空の継続トークンが返されます。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-type-name [必須]| アプリケーションの種類名。|
| --application-type-version        | アプリケーションの種類のバージョン。|
| --continuation-token           | 継続トークンのパラメーターは、次の結果セットを取得するために使用されます。 システムからの結果が 1 つの応答に収まらないときに、空以外の値を持つ継続トークンが API の応答に含まれます。 この値が次の API 呼び出しに渡されると、API が次の結果セットを返します。 それ以上の結果がない場合は、継続トークンに値が含まれません。 このパラメーターの値を URL にエンコードすることはできません。|
| --exclude-application-parameters  | アプリケーションのパラメーターを結果から除外するかどうかを指定するフラグ。|
| --max-results                  | ページング クエリの一部として返される結果の最大数。 このパラメーターは、返される結果の数に上限を定義します。 返された結果が、構成で定義したメッセージの最大サイズの制限に収まらない場合は、指定した最大結果数よりも少なくなる場合があります。 このパラメーターがゼロまたは指定されていない場合、ページング クエリには、応答メッセージに収まるできるだけ多くの結果が含まれます。|
| --timeout -t                   | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                        | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                      | このヘルプ メッセージを表示して終了します。|
| --output -o                    | 出力形式。  使用できる値は、json、jsonc、table、tsv です。               既定値は json です。|
| --query                        | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose                      | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-unprovision"></a>sfctl application unprovision
Service Fabric アプリケーションの種類をクラスターから削除または登録解除します。

Service Fabric アプリケーションの種類をクラスターから削除または登録解除します。 この操作は、アプリケーションの種類のすべてのアプリケーション インスタンスが削除されている場合にのみ実行できます。 アプリケーションの種類が登録解除されると、この特定のアプリケーションの種類に対して新しいアプリケーション インスタンスを作成できません。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --application-type-name    [必須]| アプリケーションの種類名。|
| --application-type-version [必須]| アプリケーション マニフェストで定義されているアプリケーションの種類のバージョンです。|
|--async-parameter                    | プロビジョニング解除を非同期に実行する必要があるかどうかを示すフラグです。 true に設定すると、システムによって要求が受け付けられるとプロビジョニング解除操作は戻り、タイムアウト制限なしに続行されます。 既定値は false です。 ただし、プロビジョニングされた大規模なアプリケーション パッケージの場合は、true に設定することをお勧めします。|
| --timeout -t                      | サーバー タイムアウト (秒)。  既定値は 60 です。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                           | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                         | このヘルプ メッセージを表示して終了します。|
| --output -o                       | 出力形式。  使用できる値は、json、jsonc、table、tsv です。                  既定値は json です。|
| --query                           | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose                         | ログ記録の詳細度を上げます。 完全なデバッグ ログには --debug を使用します。|

## <a name="sfctl-application-upgrade"></a>sfctl application upgrade
Service Fabric クラスターで、アプリケーションのアップグレードを開始します。

指定されたアプリケーションのアップグレード パラメーターを検証し、パラメーターが有効であれば、アプリケーションのアップグレードを開始します。 アップグレードの説明により、既存のアプリケーションの説明が置き換えられます。 これは、パラメーターが指定されていない場合、アプリケーションの既存のパラメーターが空のパラメーター リストで上書きされることを意味します。 これにより、アプリケーションがアプリケーション マニフェストからのパラメーターの既定値を使用することになります。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --app-id             [必須]| アプリケーションの ID。 これは通常、'fabric:' URI スキームのないアプリケーションの完全な名前です。 バージョン 6.0 以降では、階層名は '~' 文字で区切られます。 たとえば、アプリケーション名が "fabric:/myapp/app1" の場合、6.0 以降ではアプリケーション ID は "myapp~app1" になり、前のバージョンでは "myapp/app1" になります。|
| --app-version [必須]| ターゲットとするアプリケーションのバージョン。|
| --parameters [必須]| アプリケーションのアップグレード時に適用される、アプリケーション パラメーター オーバーライドの JSON でエンコードされた一覧。|
| --default-service-health-policy| サービスの種類の正常性を評価するために既定で使用される正常性ポリシーの JSON でエンコードされた仕様。|
| --failure-action            | 監視対象のアップグレードで監視ポリシー違反または正常性ポリシー違反が発生した場合に実行するアクション。|
| --force-restart             | コードのバージョンが変更されていない場合でも、アップグレード時にプロセスを強制的に再起動します。|
| --health-check-retry-timeout| アプリケーションまたはクラスターが正常でない場合に、正常性評価を再試行する時間。この時間を超えると、failure-action に指定したアクションが実行されます。 ミリ秒で測定されます。  既定値: PT0H10M0S。|
| --health-check-stable-duration | アプリケーションまたはクラスターが正常な状態である必要がある時間。この時間を超えると、アップグレードが次のアップグレード ドメインに進みます。            ミリ秒で測定されます。  既定値: PT0H2M0S。|
| --health-check-wait-duration| ドメインのアップグレードを完了後、待機する時間。この時間を超えると、正常性ポリシーが適用されます。 ミリ秒で測定されます。            既定値: 0。|
| --max-unhealthy-apps        | 異常なデプロイ済みアプリケーションの割合の最大許容パーセンテージ。 0 ～ 100 の数値として表されます。|
| --mode                      | ローリング アップグレード時に正常性を監視するために使用されるモード。            既定値は UnmonitoredAuto です。|
| --replica-set-check-timeout | アップグレード ドメインの処理をブロックし、予期しない問題が発生したときに可用性の損失を防ぐための最長時間。 秒単位で測定されます。|
| --service-health-policy     | サービスの種類名ごとにサービスの種類の正常性ポリシーを持つ JSON でエンコードされたマップ。 このマップは、既定では空です。|
| --timeout -t                | サーバー タイムアウト (秒)。  既定値は 60 です。|
| --upgrade-domain-timeout    | 各ドメインがアップグレードを完了する必要がある時間。この時間を超えると、FailureAction が実行されます。 ミリ秒で測定されます。  既定値: P10675199DT02H48M05.4775807S。|
| --upgrade-timeout           | アップグレード全体を完了する必要がある時間。この時間を超えると、FailureAction が実行されます。 ミリ秒で測定されます。  既定値: P10675199DT02H48M05.4775807S。|
| --warning-as-error          | 正常性評価警告をエラーと同じ重大度で処理します。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug                     | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h                   | このヘルプ メッセージを表示して終了します。|
| --output -o                 | 出力形式。  使用できる値は、json、jsonc、table、tsv です。            既定値は json です。|
| --query                     | JMESPath クエリ文字列。 詳細と例については、http://jmespath.org/ をご覧ください。|
| --verbose                   | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="sfctl-application-upload"></a>sfctl application upload
Service Fabric アプリケーション パッケージをイメージ ストアにコピーします。

必要に応じて、パッケージ内の各ファイルのアップロードの進行状況を表示します。 アップロードの進行状況は `stderr` に送信されます。

### <a name="arguments"></a>引数

|引数|[説明]|
| --- | --- |
| --path [必須]| ローカル アプリケーション パッケージへのパス。|
|--imagestore-string| アプリケーション パッケージのアップロード先のイメージ ストア。  既定値: fabric:ImageStore。|
| --show-progress  | 大きいパッケージのファイル アップロードの進行状況を表示します。|

### <a name="global-arguments"></a>グローバル引数

|引数|[説明]|
| --- | --- |
| --debug       | すべてのデバッグ ログを表示するため、ログ記録の詳細度を上げます。|
| --help -h     | このヘルプ メッセージを表示して終了します。|
| --output -o   | 出力形式。  使用できる値は、json、jsonc、table、tsv です。  既定値は json です。|
| --query       | JMESPath クエリ文字列。 詳細については、http://jmespath.org/ を参照してください。|
| --verbose     | ログ記録の詳細度を上げます。 すべてのデバッグ ログを得るには --debug を使用します。|

## <a name="next-steps"></a>次の手順
- Service Fabric CLI を[セットアップ](service-fabric-cli.md)します。
- [サンプル スクリプト](/azure/service-fabric/scripts/sfctl-upgrade-application)を使用して、Service Fabric CLI の使用方法を学習します。
