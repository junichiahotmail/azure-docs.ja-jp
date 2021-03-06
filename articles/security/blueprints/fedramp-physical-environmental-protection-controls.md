---
title: "Azure のセキュリティとコンプライアンスのブループリント - FedRAMP Web アプリケーションの自動化 - 物理的および環境的な保護"
description: "FedRAMP Web アプリケーションの自動化 - 物理的および環境的保護"
services: security
documentationcenter: na
author: jomolesk
manager: mbaldwin
editor: tomsh
ms.assetid: 0bf8349b-450d-413c-a535-6f7b80b82781
ms.service: security
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/08/2018
ms.author: jomolesk
ms.openlocfilehash: 792b9da0f4e5ec73c39f56a6e4805cf3c37133c4
ms.sourcegitcommit: 4723859f545bccc38a515192cf86dcf7ba0c0a67
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="physical-and-environmental-protection-pe"></a>物理的および環境的保護 (PE)

> [!NOTE]
> この管理策は、NIST および米国商務省により、NIST Special Publication 800-53 Revision 4 の一部として定義されています。 各コントロールのテスト手順とガイダンスについては、NIST 800-53 Rev. 4 を参照してください。

## <a name="nist-800-53-control-pe-1"></a>NIST 800-53 Control PE-1

#### <a name="physical-and-environmental-protection-policy-and-procedures"></a>物理的および環境的保護に関するポリシーと手順

**PE-1** 組織は、目的、範囲、役割、責任、経営コミットメント、組織エンティティ間の調整、およびコンプライアンスに対処した物理的および環境的保護に関するポリシーとそれに関する物理的および環境的保護の実装を促進するための手順を開発して文書化し、[割り当て: 組織で定義された担当者または役割]に周知徹底します。また、現在の物理的および環境的保護ポリシーを[割り当て: 組織で定義された頻度]で、および物理的および環境的保護の手順を[割り当て: 組織で定義された頻度]でレビューおよび更新します。

**責任:** `Customer Only`

|||
|---|---|
| **お客様** | 顧客のエンタープライズ レベルの物理的および環境的保護に関するポリシーと手順は、このコントロールに対処するために十分である可能性があります。 |
| **プロバイダー (Microsoft Azure)** | 適用外 |


 ## <a name="nist-800-53-control-pe-2a"></a>NIST 800-53 Control PE-2.a

#### <a name="physical-access-authorizations"></a>物理的なアクセスの承認

**PE-2.a** 組織は、情報システムが存在する施設にアクセスする権限を持つ個人の一覧を作成、承認し、管理します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft データセンターへの物理的なアクセスは、データセンター アクセス ツールを使用してデータセンター管理 (DCM) チームの承認を受ける必要があります。 アクセスの割り当てには、その後アクセスが自動的に削除されて再承認が必要となる、終了日が必要です。 さらに、アクセスが不要になったときは、データセンター セキュリティ責任者または管理者がアクセスの手動での終了を要求します。 |


 ## <a name="nist-800-53-control-pe-2b"></a>NIST 800-53 Control PE-2.b

#### <a name="physical-access-authorizations"></a>物理的なアクセスの承認

**PE-2.b** 組織は施設にアクセスするための承認資格情報を発行します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 データセンター アクセス ツールは、特定のデータセンターにアクセスする権限を持つすべての個人の一覧を表示する、正式なソースです。 このツールは、データセンターの物理的なセキュリティ アクセス制御装置とリンクし、DCM チームによって承認されているアクセス レベルに基づいてアクセスを承認します。 アクセス レベルは、このツールで、Microsoft 発行のユーザーのバッジまたはコントロール ルーム監督者 (CRS) によってデータセンターで割り当てられる一時的なアクセス バッジのいずれかに割り当てられます。 アクセス レベルは DCM チームによって承認されます。 データセンターの一部のエリアには、物理的なバッジに割り当てられている資格情報だけでなく、ユーザーの生体認証データ (掌形認識または指紋) の登録が必要です。 |


 ## <a name="nist-800-53-control-pe-2c"></a>NIST 800-53 Control PE-2.c

#### <a name="physical-access-authorizations"></a>物理的なアクセスの承認

**PE-2.c** 組織は、施設へのアクセスが承認された個人について詳述したアクセス リストを、[割り当て: 組織で定義された頻度]でレビューします。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 パート a で説明されているアクセスの失効に加え、Microsoft Azure では、必要に応じて個人のアクセス権を削除/更新するために、Azure データセンターの承認済みのアクセス リストを 90 日ごとにレビューします。 |


 ## <a name="nist-800-53-control-pe-2d"></a>NIST 800-53 Control PE-2.d

#### <a name="physical-access-authorizations"></a>物理的なアクセスの承認

**PE-2.d** 組織は、アクセスが不要になったときに、施設へのアクセス リストから個人を削除します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、アクセス権の割り当ての期限に達したときには、自動的にアクセス権を削除します。 アクセスが不要になったときは、データセンター セキュリティ責任者または管理者がデータ センター アクセス ツールでアクセス権の手動での終了を要求します。 さらに、Microsoft Azure は、パート c で説明されているアクセス リストのレビューの結果、すべての不要とされたアクセスの承認を削除します。 |


 ## <a name="nist-800-53-control-pe-3a"></a>NIST 800-53 Control PE-3.a

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.a** 組織は、施設へのアクセス権を付与する前に個々のアクセスの承認を検証し、かつ、[選択項目 (1 つまたは複数): [割り当て: 組織で定義された物理的なアクセスの制御システム/装置]; 警備]を使用して施設への進入/退出を制御することによって、[割り当て: 情報システムが配置されている施設への、組織が定義した入口/出口]の物理的なアクセスの承認を実施します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、24 時間 365 日体制でのスタッフ配置、警報、監視カメラ、多要素認証、およびマントラップ ポータル デバイスを使用して、Azure データセンターのあらゆる物理的なアクセス ポイントに対して物理的なアクセスの承認を実施します。 |


 ## <a name="nist-800-53-control-pe-3b"></a>NIST 800-53 Control PE-3.b

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.b** 組織は、[割り当て: 組織で定義された入口/出口]の入退出のログ記録を管理します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Azure データセンター施設への入退出は、すべてログに記録され、監査されます。 |


 ## <a name="nist-800-53-control-pe-3c"></a>NIST 800-53 Control PE-3.c

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.c** 組織は、施設内の指定された公共エリアへのアクセスを制御するために、[割り当て: 組織で定義されたセキュリティ]を提供します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Azure データセンターに、公共エリアはありません。 |


 ## <a name="nist-800-53-control-pe-3d"></a>NIST 800-53 Control PE-3.d

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.d** 組織は、訪問者に同行し、[割り当て: 組織で定義された訪問者の同行と監視に必要な環境]での訪問者の行動を監視します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 データセンターへのアクセスが承認されているすべての訪問者 (PE-2 を参照) は、バッジやその他の目印 (色付きのバッジ)などによって、「同行者必要」と指定され、常に自分の同行者から離れないでいることが求められています。 同行者のいる訪問者にはいかなるアクセス レベルも付与されず、同行者のアクセス権に基づいてのみ移動が可能です。 同行により、データセンター内での訪問者のすべての行動を監視します。 |


 ## <a name="nist-800-53-control-pe-3e"></a>NIST 800-53 Control PE-3.e

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.e** 組織は、キー、組み合わせ、およびその他の物理的なアクセス デバイスを保護します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 物理的なキーと一時的なアクセス バッジは、セキュリティ オペレーション センター (SOC) 内で保護されます。 セキュリティ責任者は、24 時間 365 日体制で配置されます。 キーは、ユーザーのアクセス バッジを物理的なキーと照合することによって特定の個人を照合します。 キーのインベントリ作成は各シフト中に行われ、キーを現場から持ち出すことは禁止されています。 |


 ## <a name="nist-800-53-control-pe-3f"></a>NIST 800-53 Control PE-3.f

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.f** 組織は、[割り当て: 組織で定義された物理的なアクセス デバイス]を[割り当て: 組織で定義された頻度]ごとにインベントリを作成します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Azure データセンター内の物理的なアクセス デバイスのインベントリは、少なくとも 1 年ごとに作成されます。 キーと一時的アクセス バッジは、各シフト中に 1 日複数回インベントリが作成されます。 アクセス バッジ リーダーなどのアクセス デバイスは、状況が常時監視されている物理的なセキュリティ システムにリンクされています。 |


 ## <a name="nist-800-53-control-pe-3g"></a>NIST 800-53 Control PE-3.g

#### <a name="physical-access-control"></a>物理的なアクセスの制御

**PE-3.g** 組織は、[割り当て: 組織で定義された頻度]、またはキーを紛失した場合、組み合わせが改ざんされた場合、あるいは個人が移動または退職した場合、組み合わせとキーを変更します。  

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データ センターには、アクセス バッジまたはキーを紛失した場合、職員が退職または移動した場合の実施手順があります。 退職または移動が発生した場合、その職員のアクセス権は直ちにシステムから削除され、そのアクセス バッジは削除されます。 |


 ### <a name="nist-800-53-control-pe-3-1"></a>NIST 800-53 Control PE-3 (1)

#### <a name="physical-access-control--information-system-access"></a>物理的なアクセスの制御 | 情報システムへのアクセス

**PE-3 (1)** 組織は、[割り当て: 情報システムの 1 つまたは複数のコンポーネントが含まれている、組織で定義された物理的スペース]にある施設に対する物理的なアクセスの制御に加え、情報システムへの物理的なアクセスの承認を実施します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、電子アクセスの制御、生体認証デバイス、アンチパスバック制御などの各種セキュリティ メカニズムによって、重要なシステムが含まれている Microsoft データ センター内のエリア (コロケーション、クリティカルな環境、MDF ルームなど) へのアクセスをさらに厳重に制御します。 Azure コロケーションへのアクセス権は、データ センターの他のアクセス エリアよりも高いレベルの、独立した DCAT アクセス権として付与されます。 さらに、Azure Government コロケーションへのアクセス権を持つすべての Azure FTE およびベンダーは、環境へのアクセスの承認を受ける前に、Microsoft のクラウド審査および米国市民権の検証を正式に受ける必要があります。 Azure Government コロケーションクラウド審査関する詳細については、PS 03 セクションをご覧ください。 |


 ## <a name="nist-800-53-control-pe-4"></a>NIST 800-53 Control PE-4

#### <a name="access-control-for-transmission-medium"></a>転送メディアに対するアクセスの制御

**PE-4** 組織は、[割り当て: 組織で定義されたセキュリティ保護]を使用して、組織の施設内の[割り当て: 組織で定義された情報システムの配電線および送信ライン]への物理的なアクセスを制御します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure の主端子盤 (MDF) ルームおよびコロケーションには、伝送メディアに対するアクセス制御を実装し、偶発的な破損、寸断物理的な改ざんから保護するための設計が施されています。 MDF ルームおよびコロケーションへのアクセスには、2 要素認証 (アクセス バッジと生体認証) が必要です。 これにより、アクセスが承認されている職員のみに制限されていることが保証されます (PE-2、PE-3 を参照)。 Mdf 内では、伝送回路および配電線は、偶発的な破損、寸断、および金属製のコンジット、施錠されたラック、ケージ、またはケーブル トレイを使用して物理的な改ざんから保護されています。 |


 ## <a name="nist-800-53-control-pe-5"></a>NIST 800-53 Control PE-5

#### <a name="access-control-for-output-devices"></a>出力デバイスのアクセスの制御

**PE-5** 組織は、承認されていない個人が出力を取得することを防ぐために、情報システムの出力デバイスへの物理的なアクセスを制御します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データセンターには、 Azure 資産または Azure 共有資産に常時接続されている出力デバイス (モニター、プリンター、オーディオ デバイスなど) はありません。 出力デバイスがないことに加え、セキュリティ責任者は、施設の物理的な実地検証を行って、施錠されるべきドアや固定されているべきラックなどの項目をシフトごとに複数回点検します。 データセンターへのアクセスは、アクセス許可が承認されている人に制限されます。 コロケーションにアクセスするには、2 要素認証 (アクセス バッジと生体認証) が必要です。 |


 ## <a name="nist-800-53-control-pe-6a"></a>NIST 800-53 Control PE-6.a

#### <a name="monitoring-physical-access"></a>物理的なアクセスの監視

**PE-6.a** 組織は、物理的なセキュリティ インシデントを検出し対応するために、情報システムが配置されている施設への物理的なアクセスを監視します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 物理的なアクセスは、データセンターにセキュリティ デバイスとプロセスを実装することによって監視されます。 例として、アクセスの24 時間 365 日体制での電子監視、アラーム、ビデオ システム、施設および敷地内の 24 時間 365 日のセキュリティ パトロールがあります。 コントロール ルーム監督者は、データセンターの物理的なアクセスの監視を行うため、常時 SOC に配置されます。 |


 ## <a name="nist-800-53-control-pe-6b"></a>NIST 800-53 Control PE-6.b

#### <a name="monitoring-physical-access"></a>物理的なアクセスの監視

**PE-6.b** 組織は、[割り当て: 組織で定義された頻度]で、および[割り当て: 組織で定義されたイベントまたは潜在的なイベントの兆候]の発生時に、物理的なアクセス ログをレビューします。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 物理的なアクセス ログは、常時確認され、以降の調査レビューのために保管されます。 |


 ## <a name="nist-800-53-control-pe-6c"></a>NIST 800-53 Control PE-6.c

#### <a name="monitoring-physical-access"></a>物理的なアクセスの監視

**PE-6.c** 組織は、組織のインシデント レスポンス機能を備えたレビューおよび調査の結果をまとめます。 

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 データセンター内で発生するセキュリティ イベントは、セキュリティ チームによって文書化されます。 セキュリティ チームは、イベントの発生後にセキュリティ イベントの詳細を捉えるレポートを作成します。 <br /> 政府機関への報告を必要とするインシデントの場合は、政府機関の顧客、米国 CERT、および米国 CERT ガイドライン内の FedRAMP に通知するために、Microsoft Azure セキュリティ チームが主要なアプリケーション プロバイダ (O365 など) とともに調整します (IR-6 を参照)。 |


 ### <a name="nist-800-53-control-pe-6-1"></a>NIST 800-53 Control PE-6 (1)

#### <a name="monitoring-physical-access--intrusion-alarms--surveillance-equipment"></a>物理的なアクセスの監視 | 侵入警報装置/監視装置

**PE-6 (1)** 組織は、物理的な侵入警報装置と監視装置を監視します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 24 時間 365 日体制の現場セキュリティに加え、Microsoft Azure データセンター (リースおよびフルマネージド) は、警報監視システムと CCTV も利用します。 警報は、SOC に 24 時間 365 日体制で常駐しているコントロール ルーム監督者が監視および応答します。 コントロール ルーム監督者は、応答中は、調査中のインシデントのエリアでカメラを使用して、応答側にリアルタイムの情報を提供します。 |


 ### <a name="nist-800-53-control-pe-6-4"></a>NIST 800-53 Control PE-6 (4)

#### <a name="monitoring-physical-access--monitoring-physical-access-to-information-systems"></a>物理的なアクセスの監視 | 情報システムへの物理的なアクセスの監視

**PE-6 (4)** 組織は、[割り当て: 情報システムの 1 つまたは複数のコンポーネントが含まれている、組織で定義された物理的スペース]としての施設の物理的なアクセスの監視に加え、情報システムへの物理的なアクセスを監視します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、施設およびデータセンター内の情報システムへの物理的なアクセスを監視します。 Microsoft のすべてのオンライン サービスの機器は、物理的なアクセスが監視されているデータセンター内に配置されます。 すべてのコロケーションおよび MDF ルームは、アクセスの制御、警報、およびビデオによって保護されます。 |


 ## <a name="nist-800-53-control-pe-8a"></a>NIST 800-53 Control PE-8.a

#### <a name="visitor-access-records"></a>訪問者のアクセスの記録

**PE-8.a** 組織は、情報システムが[割り当て: 組織で定義された期間]の間保持される施設への訪問者によるアクセスの記録を保持します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 データセンターへのアクセス記録は、データセンター アクセス ツールで、承認済みの要求の形式で保持されます。 PE-3 に記載されているように、訪問者には常に同行者が必要です。 データセンター内の同行者のアクセスはログに記録され、必要に応じて将来のレビューのために訪問者に関連付けることができます。 |


 ## <a name="nist-800-53-control-pe-8b"></a>NIST 800-53 Control PE-8.b

#### <a name="visitor-access-records"></a>訪問者のアクセスの記録

**PE-8.b** 組織は、訪問者のアクセス記録を[割り当て: 組織で定義された頻度]でレビューします。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 承認済みのアクセス要求を持つ訪問者は、政府が発行した ID または Microsoft が発行したバッジの形式と照合して身元が確認され、そのアクセス記録がレビューされます。 PE-3 に記載されているように、データセンター内で訪問者には常時同行します。 |


 ### <a name="nist-800-53-control-pe-8-1"></a>NIST 800-53 Control PE-8 (1)

#### <a name="visitor-access-records--automated-records-maintenance--review"></a>訪問者のアクセス記録 | 記録の自動メンテナンス/レビュー

**PE-8 (1)** 組織は、訪問者のアクセス記録のメンテナンスとレビューを容易にするために、自動化されたメカニズムを採用します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、承認済みの DCAT 要求の形式で DCAT 内のデータセンターのアクセス記録を保持します。 DCAT 要求は、DCM チームのみが承認できます。 データセンター内のアクセス レベルは、DCAT 内で割り当てられ管理されます。 データセンターへのアクセスは四半期ごとにレビューされます。 Azure データセンターへのすべてのアクセスは DCAT に記録され、将来の調査ために利用可能です。 訪問者には常に同行者が必要です。 データセンター内の同行者のアクセスは警報監視システムのログに記録され、必要に応じて将来のレビューのために訪問者に関連付けることができます。 訪問者のアクセスは、割り当てられた同行者によって、およびコントロール ルーム監督者が CCTV と警報監視システムを使用して、常に確認されます。 訪問者にはアクセス権は与えられず、常に同行者が同行する必要があります。 |


 ## <a name="nist-800-53-control-pe-9"></a>NIST 800-53 Control PE-9

#### <a name="power-equipment-and-cabling"></a>電源装置およびケーブル

**PE-9** 組織は、情報システムの電源装置と電源ケーブルを損傷および破壊から保護します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、保護用のスペースと適切なケーブルのラベルを提供します。 Microsoft Azure インフラストラクチャ機器 (ケーブル、電気線、およびバックアップ ジェネレーターなど) は、盗難、火災、爆発物、煙、水、ほこり、振動、地震、有害な化学薬品、電気的な干渉、停電、電源障害 (スパイク) などの環境上のリスクから保護するよう設計されている環境に配置する必要があります。 すべてのオンライン サービスのポータブル資産 (ラック、サーバー、ネットワーク デバイスなど) は、盗難や移動による破損に対して保護するために、施錠または適切な場所に固定されている必要があります。 Microsoft Azure 環境内の電源および情報システムのケーブルは、適切にラベルが付けられ、遮断または破損から保護されています。 電源および情報のケーブルは、干渉を避けるために環境内のすべてのポイントで互いに分離されています。 |


 ## <a name="nist-800-53-control-pe-10a"></a>NIST 800-53 Control PE-10.a

#### <a name="emergency-shutoff"></a>緊急遮断

**PE-10.a** 組織は、緊急事態に情報システムまたは個々のシステム コンポーネントへの電力を遮断する機能を用意します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、現地の消防規則に従って、データセンター内の適切な場所に緊急電源オフ (EPO) ボタンを設置しています。 Microsoft Azure が管理する一部のデータセンターでは、データセンターの設計に EPO ボタンの必要はなくなっています。 |


 ## <a name="nist-800-53-control-pe-10b"></a>NIST 800-53 Control PE-10.b

#### <a name="emergency-shutoff"></a>緊急遮断

**PE-10.b** 組織は、職員が安全かつ容易にアクセスできるよう、緊急遮断スイッチまたは装置を[割り当て: 情報システム別またはシステム コンポーネント別に組織で定義された場所]に配置します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 EPO ボタンは、緊急時にアクティブ化できるように考えて配置されています。 EPO ボタンは、コロケーション、有人の施設オペレーション センター (FOC)、または現地の消防規則に従って配置できます。 |


 ## <a name="nist-800-53-control-pe-10c"></a>NIST 800-53 Control PE-10.c

#### <a name="emergency-shutoff"></a>緊急遮断

**PE-10.c** 組織は、承認されていない作動から緊急電源遮断機能を保護します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 偶発的なアクティブ化を防ぐために、EPO ボタンには、保護ケースを付けたり、二重のアクティブ化を必要としたり、アクティブ化の前に警告として警報音を利用したりすることもできます。 さらに、EPO ボタンは監視カメラで記録されています。 |


 ## <a name="nist-800-53-control-pe-11"></a>NIST 800-53 Control PE-11

#### <a name="emergency-power"></a>非常用電源

**PE-11** 組織は、1 次電源の喪失に備えて、[選択項目 (1 つまたは複数): 情報システムの通常のシャット ダウン; 情報システムの長期的な代替電源への切り替え]を容易にするために短期的な無停電電源装置を用意します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、ジェネレーターの稼働を開始できるようになるまでの電源を供給するために、短期的に電源を提供する無停電電源装置 (UPS) システムでデータセンターの機器と回路を保護することによって、非常用電源を実装します。 |


 ### <a name="nist-800-53-control-pe-11-1"></a>NIST 800-53 Control PE-11 (1)

#### <a name="emergency-power--long-term-alternate-power-supply---minimal-operational-capability"></a>非常用電源 | 長期的な代替電源装置 - 最小限の運用機能

**PE-11 (1)** 組織は、1 次電源の長時間の喪失に備えて、最小限必要な稼働能力を維持できる、情報システムの長期的な代替電源装置を提供します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、1 次電源の長時間の喪失が発生したときに最小限必要な稼働能力を維持できる、情報システムの長期的な代替電源装置を実装します。 停電時または許容できない電圧レベルになったときは、無停電電源装置 (UPS) システムが瞬時に作動して電力負荷を引き継ぎます。 これは、ジェネレーターが引き継ぐことができるようになるまでサーバーを実行するために十分な電力を提供します。 非常用ジェネレーターは、長時間の停電および計画的なメンテナンスのためのバックアップ電源を提供し、自然災害が発生した場合に備えて現場の予備燃料を使ってデータセンターを稼働することができます。 Azure は、多くのデータセンターでディーゼル ジェネレーターを保持しています。 バックアップ ジェネレーターは、送電系統の安定性を守るため、または臨時の修理に必要な場合、およびデータセンターを送電網から外す必要のあるメンテナンスの際に使用されます。 |


 ## <a name="nist-800-53-control-pe-12"></a>NIST 800-53 Control PE-12

#### <a name="emergency-lighting"></a>非常用照明

**PE-12** 組織は、停電または寸断の発生時に作動する情報システムと施設内の非常口と避難経路用の自動非常用照明を設置し管理します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データセンター (リースおよびフルマネージド) は、UPS とジェネレーター システム (PE-11 を参照) によってバックアップされる専用回線の頭上の非常用照明の形で非常用照明を実装します。 自動非常用照明は、National Fire Protection Association (NFPA) Life Safety Code に従って、すべての避難経路、非常口の周辺、およびコロケーション内部に設置されています。 ユーティリティ電源が失われた場合、非常用照明は自動的に UPS およびジェネレーター システムによって供給される電源に切り替わります。 Microsoft Azure データセンター内の非常用照明システムは、適切に作動する状態を確実に維持するために、定期的なメンテナンスが行われます。 |


 ## <a name="nist-800-53-control-pe-13"></a>NIST 800-53 Control PE-13

#### <a name="fire-protection"></a>防火

**PE-13** 組織は、独立したエネルギー源によってサポートされている、情報システム用の消火および検知装置/システムを採用し、管理します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、Microsoft Azure データセンターに火災検知および消火システムを設置することによって防火対策を実施しています。 <br /> Microsoft Azure データセンターは、堅牢な火災検知メカニズムを組み入れています。 Microsoft Azure の防火のアプローチには、防火スプリンクラー システムと統合されている床下と天井に取り付けられた光電式煙探知器の使用が含まれています。 さらに、各コロケーションに空気を監視する Xtralis VESDA (Very Early Smoke Detection Apparatus) システムがあります。 VESDA ユニットは、複数の高価値のスペース全体に設置された高感度のエア サンプリング システムです。 VESDA ユニットでは、実際の火災検知警報の前に調査応答が可能です。 <br /> 手動の火災警報通知用に、データセンター全体に「プル ステーション」の火災警報ボックスが設置されています。 データセンター全体に消火器が配置されていて、年 1 回適切に検査、点検、およびタグ付けされています。 セキュリティ担当者は、建物のすべてのエリアをシフトごとに複数回パトロールします。 データセンターの職員は、毎日現場の点検を行って、すべての火災監視要件を確実に満たします。 <br /> 精密な電気機器が備えられているエリア (コロケーションや MDF など) は、ダブル インターロック プリアクション (ドライ パイプ) スプリンクラー システムで保護されています。 ドライ パイプ スプリンクラーは、スプリンクラーヘッドの作動 (熱による) と煙検知による水の放出の両方を必要とする、2 段階プリアクション システムです。 スプリンクラー ヘッドの作動は、パイプを水で満たすことができるようにするパイプ内の空気圧を放出します。 水は煙または熱検知器も作動したときに放出されます。 <br /> 火災検知/消火および非常用照明システムは、冗長電源を提供するデータセンターの UPS およびジェネレーター システムにつながっています。 |


 ### <a name="nist-800-53-control-pe-13-1"></a>NIST 800-53 Control PE-13 (1)

#### <a name="fire-protection--detection-devices--systems"></a>防火 | 探知装置/システム

**PE-13 (1)** 組織は、火災発生時に自動的に作動して[割り当て: 組織で定義された職員または役割]および[割り当て: 組織で定義された緊急時対応要員]に通知する、情報システム用の火災検知装置を採用しています。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、火災発生時に自動的に作動し、緊急時対応要員とともにデータセンターの職員に通知する、情報システム用の火災検知装置を採用しています。 コロケーションで火災検知メカニズムのいずれかが作動した場合は、火災警報システムによって現地の消防署に自動的に通報されます。 加えて、防火および火災検知システムは、現地の施設およびセキュリティ要員に通知するセキュリティ システムと連携しています。 |


 ### <a name="nist-800-53-control-pe-13-2"></a>NIST 800-53 Control PE-13 (2)

#### <a name="fire-protection--suppression-devices--systems"></a>防火 | 消火装置/システム

**PE-13 (2)** 組織は、[割り当て: 組織で定義された職員または役割]および[割り当て: 組織で定義された緊急時対応要員]に自動的に通知する、情報システム用の消火装置/システムを採用します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 データセンターで消火システムのいずれかが作動した場合は、火災警報システムによって現地の消防署に自動的に通報されます。 加えて、防火および火災検知システムは、現地の施設およびセキュリティ要員に通知するセキュリティ システムと連携しています。 |


 ### <a name="nist-800-53-control-pe-13-3"></a>NIST 800-53 Control PE-13 (3)

#### <a name="fire-protection--automatic-fire-suppression"></a>防火 | 自動消火装置

**PE-13 (3)** 組織は、施設の要員が常時配置されているわけではない場合は、情報システム用の自動消火機能を採用します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データセンターには 24 時間 365 日体制で要員が配置されています。 消火システムは、火災警報の状況が検知されたときに、手動による介入なしで自動的に発動します。 |


 ## <a name="nist-800-53-control-pe-14a"></a>NIST 800-53 Control PE-14.a

#### <a name="temperature-and-humidity-controls"></a>温湿度制御

**PE-14.a** 組織は、情報システムが[割り当て: 組織で定義された許容レベル]に置かれている施設内の温度および湿度のレベルを維持します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、米国暖房冷凍空調学会 (ASHRAE) のガイドラインに従って温度と湿度レベルを維持します。 温度と湿度のレベルはデータセンターの建物管理システム (BMS) によって常時監視されています。 |


 ## <a name="nist-800-53-control-pe-14b"></a>NIST 800-53 Control PE-14.b

#### <a name="temperature-and-humidity-controls"></a>温湿度制御

**PE-14.b** 組織は、温度と湿度のレベルを[割り当て: 組織で定義された頻度]で監視します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データセンターでは、温度と湿度のレベルは建物管理システム (BMS) によって常時監視されています。 データセンターの職員は施設オペレーション センターから BMS を監視するため、警報ポイントを超過する前にデータセンター内で温度と湿度を管理できます。 |


 ### <a name="nist-800-53-control-pe-14-2"></a>NIST 800-53 Control PE-14 (2)

#### <a name="temperature-and-humidity-controls--monitoring-with-alarms--notifications"></a>温湿度制御 | 監視と警報/通知

**PE-14 (2)** 組織は、人または機器に害を及ぼす恐れのある変化の警告または通知を行う温湿度監視を採用します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure データセンターでは、温度と湿度のレベルは建物管理システム (BMS) によって常時監視されています。 データセンターの職員は施設オペレーション センターから BMS を監視するため、警報ポイントを超過する前にデータセンター内で温度と湿度を管理できます。 |


 ## <a name="nist-800-53-control-pe-15"></a>NIST 800-53 Control PE-15

#### <a name="water-damage-protection"></a>水害からの保護

**PE-15** 組織は、アクセス可能で適切に動作し、主要な職員に知られている、マスター遮断または遮断弁を備えることによって、水漏れにつながる損傷から情報システムを保護します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、水漏れ (空気量調整器など) の危険のあるエリアで水漏れ検知を行います。 消火システムには、監視される漏水検知警報も含まれています。 水漏れ検知システムは、施設の警報および通知システムと統合されています。 データセンターのスプリンクラー システムは区画分けされています。 データセンターの職員は、止水弁の場所と緊急時の使用手順に習熟しています。 スプリンクラー ライザーには、個別または仕切弁を使ってグループで停止する機能があります。 重要なスペースにあるすべてのスプリンクラーは、放水の開始前に 二重の動作を必要とするダブル インターロック プリアクション タイプのスプリンクラーです。 スプリンクラー システムの圧力は監視され、水漏れに対して警報が出されます。 |


 ### <a name="nist-800-53-control-pe-15-1"></a>NIST 800-53 Control PE-15 (1)

#### <a name="water-damage-protection--automation-support"></a>水害からの保護 | 自動サポート

**PE-15 (1)** 組織は、情報システムの近辺の水分の有無を検知する自動メカニズムを採用して、[割り当て: 組織で定義された職員または役割]に通知します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure は、データセンターの水分の有無を検知する自動メカニズムを採用して、データ センターの職員に通知します。 Azure は、水漏れの危険のあるエリア (空気量調整器など)で水漏れ検知を行います。 消火システムには、監視される漏水検知警報も含まれています。 水漏れ検知システムは、施設の警報および通知システムと統合されています。 スプリンクラー システムの圧力は監視され、水漏れに対して警報が出されます。 |


 ## <a name="nist-800-53-control-pe-16"></a>NIST 800-53 Control PE-16

#### <a name="delivery-and-removal"></a>納入と撤去

**PE-16** 組織は、組織に出入りする[割り当て: 組織で定義された情報システム コンポーネントのタイプ]を承認、監視、および制御し、それらの品目の記録を保持します。

**責任:** `Azure Only`

|||
|---|---|
| **お客様** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Microsoft Azure が顧客に代わってこの要件を履行します。 Microsoft Azure は、データセンターへの出入りが許可されているものの厳密な適用条件を実装します。 すべてのシステム コンポーネント/資産は、資産管理ツールのデータベースで追跡されています。 |


 ## <a name="nist-800-53-control-pe-17a"></a>NIST 800-53 Control PE-17.a

#### <a name="alternate-work-site"></a>代替作業サイト

**PE-17.a** 組織は、代替作業サイトにおいて[割り当て: 組織で定義されたセキュリティ コントロール]を採用します。

**責任:** `Customer Only`

|||
|---|---|
| **顧客** | 顧客によるエンタープライズ レベルの代替作業サイトの提供は、このコントロールに対処するために十分である可能性があります。 |
| **プロバイダー (Microsoft Azure)** | 適用外 |


 ## <a name="nist-800-53-control-pe-17b"></a>NIST 800-53 Control PE-17.b

#### <a name="alternate-work-site"></a>代替作業サイト

**PE-17.b** 組織は、代替作業サイトのセキュリティ コントロールの実現性と有効性を評価します。

**責任:** `Customer Only`

|||
|---|---|
| **お客様** | 顧客によるエンタープライズ レベルの代替作業サイトの提供は、このコントロールに対処するために十分である可能性があります。 |
| **プロバイダー (Microsoft Azure)** | 適用外 |


 ## <a name="nist-800-53-control-pe-17c"></a>NIST 800-53 Control PE-17.c

#### <a name="alternate-work-site"></a>代替作業サイト

**PE-17.c** 組織は、セキュリティ インシデントや問題が発生した場合に従業員が情報セキュリティ担当者と連絡を取る手段を提供します。

**責任:** `Customer Only`

|||
|---|---|
| **顧客** | 顧客によるエンタープライズ レベルの代替作業サイトの提供は、このコントロールに対処するために十分である可能性があります。 |
| **プロバイダー (Microsoft Azure)** | 適用されません |


 ## <a name="nist-800-53-control-pe-18"></a>NIST 800-53 Control PE-18

#### <a name="location-of-information-system-components"></a>情報システム コンポーネントの場所

**PE-18** 組織は[割り当て: 組織で定義された物理的および環境上の危険]による損害を最小限に抑え、かつ、未承認のアクセスの機会を最小限に抑えるように、施設内の情報システム コンポーネントを配置します。

**責任:** `Azure Only`

|||
|---|---|
| **顧客** | 顧客は、Azure データセンターのどのシステム リソースにも物理的なアクセスはできません。 |
| **プロバイダー (Microsoft Azure)** | Azure は、情報システム コンポーネント配置のコントロールを満たすために、データセンターの戦略的な設計アプローチを実施します。 Microsoft のすべてのオンライン サービスの機器は、盗難、火災、爆発物、煙、水、ほこり、振動、地震、有害な化学薬品、電気的な干渉、停電、電源障害 (スパイク)、放射線などの環境上のリスクから保護するよう設計されている環境に配置する必要があります。 施設とインフラストラクチャには、環境上のリスクからの保護に備える地震対策が取られています。 すべてのコロケーションおよび MDF ルームは、アクセスの制御、警報、およびビデオによって保護されます。 施設では 24 時間 365 日体制でセキュリティ責任者による警備が実施されています。 運搬可能なすべての Azure 資産は、盗難や移動時の破損から保護するために、施錠または適切な位置に固定されています。 |


