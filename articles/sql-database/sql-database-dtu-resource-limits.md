---
title: Azure SQL Database の DTU ベースのリソース制限 | Microsoft Docs
description: このページでは、Azure SQL Database に対するいくつかの一般的な DTU ベースのリソース制限について説明します。
services: sql-database
author: CarlRabeler
manager: craigg
ms.service: sql-database
ms.custom: DBs & servers
ms.topic: article
ms.date: 04/04/2018
ms.author: carlrab
ms.openlocfilehash: c4c85395856756e8ec6a788aa958b479a297892d
ms.sourcegitcommit: 6fcd9e220b9cd4cb2d4365de0299bf48fbb18c17
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="azure-sql-database-dtu-based-resource-model-limits"></a>Azure SQL Database の DTU ベースのリソース モデル制限

> [!IMPORTANT]
> 仮想コアベースのリソース制限については、[SQL Database の仮想コアベースのリソース制限](sql-database-vcore-resource-limits.md)に関するページを参照してください。

## <a name="single-database-storage-sizes-and-performance-levels"></a>単一データベース: ストレージ サイズとパフォーマンス レベル

次の表では、各サービス レベルおよびパフォーマンス レベルにおいて単一データベースで使用可能なリソースを示します。 [Azure Portal](sql-database-single-database-resources.md#manage-single-database-resources-using-the-azure-portal)、[Transact-SQL](sql-database-single-database-resources.md#manage-single-database-resources-using-transact-sql)、[PowerShell](sql-database-single-database-resources.md#manage-single-database-resources-using-powershell)、[Azure CLI](sql-database-single-database-resources.md#manage-single-database-resources-using-the-azure-cli)、または [REST API](sql-database-single-database-resources.md#manage-single-database-resources-using-the-rest-api) を使って、単一のデータベースにサービス レベル、パフォーマンス レベル、ストレージ量を設定できます。

### <a name="basic-service-tier"></a>Basic サービス レベル
| **パフォーマンス レベル** | **Basic** |
| :--- | --: |
| 最大 DTU 数 | 5 |
| 付属ストレージ (GB) | 2 |
| 選択可能な最大ストレージ容量 (GB) | 2 |
| 最大インメモリ OLTP ストレージ容量 (GB) |該当なし |
| 最大同時実行ワーカー (要求) 数 | 30 |
| 最大同時ログイン数 | 30 |
| 最大同時セッション数 | 300 |
|||

### <a name="standard-service-tier"></a>Standard サービス レベル
| **パフォーマンス レベル** | **S0** | **S1** | **S2** | **S3** |
| :--- |---:| ---:|---:|---:|---:|
| 最大 DTU 数** | 10 | 20 | 50 | 100 |
| 付属ストレージ (GB) | 250 | 250 | 250 | 250 |
| 選択可能な最大ストレージ容量 (GB)* | 250 | 250 | 250 | 250、500、750、1024 |
| 最大インメモリ OLTP ストレージ容量 (GB) | 該当なし | 該当なし | 該当なし | 該当なし |
| 最大同時実行ワーカー (要求) 数| 60 | 90 | 120 | 200 |
| 最大同時ログイン数 | 60 | 90 | 120 | 200 |
| 最大同時セッション数 |600 | 900 | 1200 | 2400 |
||||||

### <a name="standard-service-tier-continued"></a>Standard サービス レベル (続き)
| **パフォーマンス レベル** | **S4** | **S6** | **S7** | **S9** | **S12** |
| :--- |---:| ---:|---:|---:|---:|---:|
| 最大 DTU 数** | 200 | 400 | 800 | 1600 | 3000 |
| 付属ストレージ (GB) | 250 | 250 | 250 | 250 | 250 |
| 選択可能な最大ストレージ容量 (GB)* | 250、500、750、1024 | 250、500、750、1024 | 250、500、750、1024 | 250、500、750、1024 | 250、500、750、1024 |
| 最大インメモリ OLTP ストレージ容量 (GB) | 該当なし | 該当なし | 該当なし | 該当なし |該当なし |
| 最大同時実行ワーカー (要求) 数| 400 | 800 | 1600 | 3200 |6000 |
| 最大同時ログイン数 | 400 | 800 | 1600 | 3200 |6000 |
| 最大同時セッション数 |4800 | 9600 | 19200 | 30000 |30000 |
|||||||

### <a name="premium-service-tier"></a>Premium サービス レベル 
| **パフォーマンス レベル** | **P1** | **P2** | **P4** | **P6** | **P11** | **P15** | 
| :--- |---:|---:|---:|---:|---:|---:|
| 最大 DTU 数 | 125 | 250 | 500 | 1,000 | 1750 | 4000 |
| 付属ストレージ (GB) | 500 | 500 | 500 | 500 | 4096 | 4096 |
| 選択可能な最大ストレージ容量 (GB)* | 500、750、1024 | 500、750、1024 | 500、750、1024 | 500、750、1024 | 4096 | 4096 |
| 最大インメモリ OLTP ストレージ容量 (GB) | 1 | 2 | 4 | 8 | 14 | 32 |
| 最大同時実行ワーカー (要求) 数| 200 | 400 | 800 | 1600 | 2400 | 6400 |
| 最大同時ログイン数 | 200 | 400 | 800 | 1600 | 2400 | 6400 |
| 最大同時セッション数 | 30000 | 30000 | 30000 | 30000 | 30000 | 30000 |
|||||||


> [!IMPORTANT]
> \* 付属のストレージ容量を超えるストレージ サイズはプレビュー段階であり、追加料金が適用されます。 詳細については、「 [SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)」をご覧ください。 
>
>\* Premium レベルでは現在、次のリージョンで 1 TB を超えるストレージが使用できます: オーストラリア東部、オーストラリア南東部、ブラジル南部、カナダ中部、カナダ東部、米国中部、フランス中部、ドイツ中部、東日本、西日本、韓国中部、米国中北部、北ヨーロッパ、米国中南部、東南アジア、英国南部、英国西部、米国東部 2、米国西部、米国政府バージニア、および西ヨーロッパ。 [P11 ～ P15 の現時点での制限](#single-database-limitations-of-p11-and-p15-when-the-maximum-size-greater-than-1-tb)に関するページを参照してください。  
> 
>\*\* Standard におけるデータベースあたりの最大 DTU 数 (200 DTU 以上) はプレビュー段階です。
>


## <a name="single-database-change-storage-size"></a>単一データベース: ストレージ サイズを変更する

- 単一データベースの DTU 価格には、追加コストなしで一定量のストレージが含まれます。 付属の容量を超える分のストレージについては、追加費用を払うことで、1 TB までは 250 GB 単位で、1 TB 以降は 256 GB 単位で、最大サイズ制限までプロビジョニングできます。 付属するストレージの量と最大サイズ制限については、「[単一データベース: ストレージ サイズとパフォーマンス レベル](#single-database-storage-sizes-and-performance-levels)」をご覧ください。
- 単一データベースの追加ストレージは、[Azure Portal](sql-database-single-database-resources.md#manage-single-database-resources-using-the-azure-portal)、[Transact-SQL](/sql/t-sql/statements/alter-database-azure-sql-database#examples)、[PowerShell](/powershell/module/azurerm.sql/set-azurermsqldatabase)、[Azure CLI](/cli/azure/sql/db#az_sql_db_update)、または [REST API](/rest/api/sql/databases/update) を使ってサイズを最大に増やすことでプロビジョニングできます。
- 単一データベースの追加ストレージの料金は、追加ストレージ量にサービス レベルの追加ストレージ単価を掛けて計算します。 追加ストレージの価格について詳しくは、「[SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)」をご覧ください。

## <a name="single-database-change-dtus"></a>単一データベース: DTU を変更する

サービス レベル、パフォーマンス レベル、およびストレージ量を最初に選択した後は、[Azure Portal](sql-database-single-database-resources.md#manage-single-database-resources-using-the-azure-portal)、[Transact-SQL](/sql/t-sql/statements/alter-database-azure-sql-database#examples)、[PowerShell](/powershell/module/azurerm.sql/set-azurermsqldatabase)、[Azure CLI](/cli/azure/sql/db#az_sql_db_update)、または [REST API](/rest/api/sql/databases/update) を使い、実際の状況に基づいて、単一データベースを動的にスケールアップまたはスケールダウンできます。 

次のビデオでは、パフォーマンス レベルを動的に変更して単一データベースで使用可能な DTU を増やす方法を示します。

> [!VIDEO https://channel9.msdn.com/Blogs/Azure/Azure-SQL-Database-dynamically-scale-up-or-scale-down/player]
>

データベースのサービス レベルやパフォーマンス レベルを変更すると、新しいパフォーマンス レベルで元のデータベースのレプリカが作成され、接続先がそのレプリカに切り替えられます。 このプロセスでデータが失われることはありませんが、レプリカに切り替えるほんの少しの間、データベースに接続できなくなるため、実行中の一部トランザクションがロールバックされる場合があります。 切り替え時間はさまざまですが、通常 4 秒以内であり、99% 以上が 30 秒未満です。 接続が無効になった時点で多数のトランザクションが実行中の場合、切り替え時間が長引くことがあります。 

スケールアップ プロセス全体の継続時間は、変更前後のデータベースのサイズとサービス レベルによって異なります。 たとえば、250 GB のデータベースを Standard サービス レベルとの間または Standard サービス レベル内で変更する場合は、6 時間以内に完了します。 Premium サービス レベル内で同じサイズのデータベースのパフォーマンス レベルを変更する場合、スケールアップは 3 時間以内で完了します。

> [!TIP]
> 実行中の操作の監視については、[SQL REST API を使った操作の管理](/rest/api/sql/Operations/List)、[CLI を使った操作の管理](/cli/azure/sql/db/op)、[T-SQL を使った操作の管理](/sql/relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database)に関する各ページと、2 つの PowerShell コマンド [Get-AzureRmSqlDatabaseActivity](/powershell/module/azurerm.sql/get-azurermsqldatabaseactivity) と [Stop-AzureRmSqlDatabaseActivity](/powershell/module/azurerm.sql/stop-azurermsqldatabaseactivity) をご覧ください。

* より上位のサービス レベルまたはパフォーマンス レベルにアップグレードしても、より大きなサイズ (最大サイズ) を明示的に指定しない限り、データベースの最大サイズは増加しません。
* データベースをダウングレードするには、データベースで使われている領域がダウングレード後のサービス レベルとパフォーマンス レベルで許可されている最大サイズより小さい必要があります。 
* **Premium** から **Standard** レベルにダウングレードするときは、(1) データベースの最大サイズがターゲットのパフォーマンス レベルでサポートされていて、かつ、(2) 最大サイズがターゲットのパフォーマンス レベルで付属のストレージ量を超えている場合、追加ストレージ コストが適用されます。 たとえば、最大サイズ 500 GB の P1 データベースを S3 にダウンサイズする場合、S3 がサポートする最大サイズは 500 GB であり、S3 で付属のストレージ量は 250 GB だけなので、追加ストレージ コストが適用されます。 したがって、追加ストレージ量は 500 GB – 250 GB = 250 GB になります。 追加ストレージの価格については、「[SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)」をご覧ください。 実際に使われる領域の量が付属のストレージの量より少ない場合、データベースの最大サイズを付属の量に減らすことで、この追加コストを回避できます。 
* [geo レプリケーション](sql-database-geo-replication-portal.md)が有効な状態でデータベースをアップグレードする場合、そのセカンダリ データベースを目的のパフォーマンス レベルにアップグレードしてから、プライマリ データベースをアップグレードします (パフォーマンスを最大にするための一般的なガイダンス)。 別のエディションにアップグレードする場合は、最初にセカンダリ データベースのアップグレードが必要です。
* [geo レプリケーション](sql-database-geo-replication-portal.md)が有効な状態でデータベースをダウングレードする場合、目的のパフォーマンス レベルにセカンダリ データベースをダウングレードしてから、プライマリ データベースをダウングレードします (パフォーマンスを最大にするための一般的なガイダンス)。 別のエディションにダウングレードする場合は、最初にプライマリ データベースのダウングレードが必要です。
* サービス階層によって、提供されている復元サービスは異なります。 **Basic** レベルにダウングレードする場合は、バックアップのリテンション期間が短くなります。「[SQL Database 自動バックアップについての詳細情報](sql-database-automated-backups.md)」をご覧ください。
* データベースに対する新しいプロパティは、変更が完了するまで適用されません。

## <a name="single-database-limitations-of-p11-and-p15-when-the-maximum-size-greater-than-1-tb"></a>単一データベース: 最大サイズが 1 TB を超える場合の P11 および P15 の制限事項

次のリージョンでは、最大サイズが 1 TB を超える P11 および P15 データベースがサポートされます。オーストラリア東部、オーストラリア南東部、ブラジル南部、カナダ中部、カナダ東部、米国中部、フランス中部、ドイツ中部、東日本、西日本、韓国中部、米国中北部、北ヨーロッパ、米国中南部、東南アジア、英国南部、英国西部、米国東部 2、米国西部、米国政府バージニア、および西ヨーロッパ。 最大サイズが 1 TB を超える P11 および P15 データベースには、次の考慮事項と制限事項が適用されます。

- データベースを作成するときに (4 TB または 4096 GB の値を使用して) 1 TB を超える最大サイズを選択した場合、サポートされていないリージョンでデータベースをプロビジョニングすると、エラーのため、create コマンドが失敗します。
- サポート対象のリージョンにある既存の P11 と P15 のデータベースでは、最大ストレージを 1 TB を超えて最大 4 TB まで 256 GB 刻みで増やすことができます。 対象リージョンでより大きなサイズがサポートされているかどうかを確認するには、[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 関数を使うかか、Azure Portal でデータベースのサイズを調べてください。 既存の P11 または P15 のデータベースのアップグレードは、サーバーレベル プリンシパルのログインまたは dbmanager データベース ロールのメンバーのみが実行できます。 
- サポートされているリージョンでアップグレード操作が実行されると、すぐに構成が更新されます。 データベースは、アップグレード処理中もオンラインのままになります。 ただし、実際のデータベース ファイルが新しい最大サイズにアップグレードされるまで、1 TB を超えるストレージの容量を完全に利用することはできません。 必要な時間は、アップグレードされるデータベースのサイズに応じて異なります。 
- P11 または P15 データベースを作成または更新するときは、1 TB から 4 TB の範囲で、256 GB 刻みでのみ最大サイズを選択できます。 P11/P15 を作成するとき、既定で 1 TB のストレージ オプションがあらかじめ選択されています。 サポート対象のリージョンにあるデータベースでは、新規または既存の単一データベースのストレージの最大サイズを最大 4 TB まで増やすことができます。 他のすべてのリージョンでは、最大サイズが 1 TB を超えることはできません。 4 TB の付属のストレージを選択しても、価格は変わりません。
- データベースの最大サイズを 1 TB より大きい値に設定した場合は、ストレージの実際の使用量が 1 TB を下回る場合でも、1 TB に変更することはできません。 したがって、最大サイズが 1 TB より大きい P11 または P15 を、1 TB の P11、1 TB の P15、またはそれより低いパフォーマンス レベル (P1-P6 など) にダウングレードすることはできません。 この制限は、ポイントインタイム リストア、geo リストア、長期的なバックアップ保有期間、データベース コピーなど、復元とコピーのシナリオにも適用されます。 データベースを 1 TB より大きい最大サイズで構成した後、そのデータベースのすべての復元操作は、最大サイズが 1 TB より大きい P11/P15 に対して実行する必要があります。
- アクティブ geo レプリケーションのシナリオの場合:
   - geo レプリケーションのリレーションシップの設定: プライマリ データベースが P11 または P15 の場合は、セカンダリも P11 または P15 である必要があります。つまり、下位のパフォーマンス レベルは、1 TB を超えるサイズをサポートできないため、セカンダリとして拒否されます。
   - geo レプリケーションのリレーションシップでのプライマリ データベースのアップグレード: プライマリ データベースで最大サイズを 1 TB 超に変更すると、セカンダリ データベースでも同じ変更がトリガーされます。 プライマリに対する変更を有効にするには、両方のアップグレードが正常に完了する必要があります。 1 TB を超えるオプションに関するリージョンの制限が適用されます。 1 TB 超をサポートしていないリージョンにセカンダリが存在する場合、プライマリはアップグレードされません。
- 1 TB を超える P11/P15 データベースの読み込みに Import/Export サービスを使うことはサポートされていません。 SqlPackage.exe を使用して、データを[インポート](sql-database-import.md)および[エクスポート](sql-database-export.md)してください。

## <a name="elastic-pool-storage-sizes-and-performance-levels"></a>エラスティック プール: ストレージ サイズとパフォーマンス レベル

次の表では、SQL Database エラスティック プールについて、各サービス レベルおよびパフォーマンス レベルで使用可能なリソースを示します。 [Azure Portal](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-the-azure-portal)、[PowerShell](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-powershell)、[Azure CLI](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-the-azure-cli)、または [REST API](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-the-rest-api) を使って、サービス レベル、パフォーマンス レベル、ストレージ量を設定できます。

> [!NOTE]
> エラスティック プール内の個々のリソース制限は、一般的に DTU やサービス層に基づくプール外の単一のデータベースのリソース制限と同じです。 たとえば、S2 データベースの最大同時実行ワーカー数は 120 ワーカーです。 そのため、プール内の各データベースの最大 DTU が 50 DTU (S2 と同じ) の場合、Standard プール内のデータベースの最大同時実行ワーカー数も 120 ワーカーです。

### <a name="basic-elastic-pool-limits"></a>Basic エラスティック プールの制限

| プールあたりの eDTU 数 | **50** | **100** | **200** | **300** | **400** | **800** | **1200** | **1600** |
|:---|---:|---:|---:| ---: | ---: | ---: | ---: | ---: |
| プールあたりの付属ストレージ (GB) | 5 | 10 | 20 | 29 | 39 | 78 | 117 | 156 |
| プールあたりの選択可能な最大ストレージ容量 (GB) | 5 | 10 | 20 | 29 | 39 | 78 | 117 | 156 |
| プールあたりの最大インメモリ OLTP ストレージ容量 (GB) | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし |
| プールあたりの最大 DB 数 | 100 | 200 | 500 | 500 | 500 | 500 | 500 | 500 |
| プールあたりの最大同時実行ワーカー (要求) 数 | 100 | 200 | 400 | 600 | 800 | 1600 | 2400 | 3200 |
| プールあたりの最大同時ログイン数 | 100 | 200 | 400 | 600 | 800 | 1600 | 2400 | 3200 |
| プールあたりの最大同時セッション数 | 30000 | 30000 | 30000 | 30000 |30000 | 30000 | 30000 | 30000 |
| データベースあたりの選択可能な最小 eDTU 数 | 0、5 | 0、5 | 0、5 | 0、5 | 0、5 | 0、5 | 0、5 | 0、5 |
| データベースあたりの選択可能な最大 eDTU 数 | 5 | 5 | 5 | 5 | 5 | 5 | 5 | 5 |
| データベースあたりの最大ストレージ (GB) | 2 | 2 | 2 | 2 | 2 | 2 | 2 | 2 | 
||||||||

### <a name="standard-elastic-pool-limits"></a>Standard エラスティック プールの制限

| プールあたりの eDTU 数 | **50** | **100** | **200** | **300** | **400** | **800**| 
|:---|---:|---:|---:| ---: | ---: | ---: | 
| プールあたりの付属ストレージ (GB) | 50 | 100 | 200 | 300 | 400 | 800 | 
| プールあたりの選択可能な最大ストレージ容量 (GB)* | 50、250、500 | 100、250、500、750 | 200、250、500、750、1024 | 300、500、750、1024、1280 | 400、500、750、1024、1280、1536 | 800、1024、1280、1536、1792、2048 | 
| プールあたりの最大インメモリ OLTP ストレージ容量 (GB) | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 
| プールあたりの最大 DB 数 | 100 | 200 | 500 | 500 | 500 | 500 | 
| プールあたりの最大同時実行ワーカー (要求) 数 | 100 | 200 | 400 | 600 | 800 | 1600 |
| プールあたりの最大同時ログイン数 | 100 | 200 | 400 | 600 | 800 | 1600 |
| プールあたりの最大同時セッション数 | 30000 | 30000 | 30000 | 30000 | 30000 | 30000 |
| データベースあたりの選択可能な最小 eDTU 数 | 0、10、20、50 | 0、10、20、50、100 | 0、10、20、50、100、200 | 0、10、20、50、100、200、300 | 0、10、20、50、100、200、300、400 | 0、10、20、50、100、200、300、400、800 |
| データベースあたりの選択可能な最大 eDTU 数 | 10、20、50 | 10、20、50、100 | 10、20、50、100、200 | 10、20、50、100、200、300 | 10、20、50、100、200、300、400 | 10、20、50、100、200、300、400、800 | 
| データベースあたりの最大ストレージ (GB)* | 500 | 750 | 1024 | 1024 | 1024 | 1024 |
||||||||

### <a name="standard-elastic-pool-limits-continued"></a>Standard エラスティック プールの制限 (続き) 

| プールあたりの eDTU 数 | **1200** | **1600** | **2000** | **2500** | **3000** |
|:---|---:|---:|---:| ---: | ---: |
| プールあたりの付属ストレージ (GB) | 1200 | 1600 | 2000 | 2500 | 3000 | 
| プールあたりの選択可能な最大ストレージ容量 (GB)* | 1200、1280、1536、1792、2048、2304、2560 | 1600、1792、2048、2304、2560、2816、3072 | 2000、2048、2304、2560、2816、3072、3328、3584 | 2500、2560、2816、3072、3328、3584、3840、4096 | 3000、3072、3328、3584、3840、4096 |
| プールあたりの最大インメモリ OLTP ストレージ容量 (GB) | 該当なし | 該当なし | 該当なし | 該当なし | 該当なし | 
| プールあたりの最大 DB 数 | 500 | 500 | 500 | 500 | 500 | 
| プールあたりの最大同時実行ワーカー (要求) 数 | 2400 | 3200 | 4000 | 5000 | 6000 |
| プールあたりの最大同時ログイン数 | 2400 | 3200 | 4000 | 5000 | 6000 |
| プールあたりの最大同時セッション数 | 30000 | 30000 | 30000 | 30000 | 30000 | 
| データベースあたりの選択可能な最小 eDTU 数 | 0、10、20、50、100、200、300、400、800、1200 | 0、10、20、50、100、200、300、400、800、1200、1600 | 0、10、20、50、100、200、300、400、800、1200、1600、2000 | 0、10、20、50、100、200、300、400、800、1200、1600、2000、2500 | 0、10、20、50、100、200、300、400、800、1200、1600、2000、2500、3000 |
| データベースあたりの選択可能な最大 eDTU 数 | 10、20、50、100、200、300、400、800、1200 | 10、20、50、100、200、300、400、800、1200、1600 | 10、20、50、100、200、300、400、800、1200、1600、2000 | 10、20、50、100、200、300、400、800、1200、1600、2000、2500 | 10、20、50、100、200、300、400、800、1200、1600、2000、2500、3000 | 
| データベースあたりの選択可能な最大ストレージ (GB)* | 1024 | 1024 | 1024 | 1024 | 1024 | 
||||||||

### <a name="premium-elastic-pool-limits"></a>Premium エラスティック プールの制限

| プールあたりの eDTU 数 | **125** | **250** | **500** | **1000** | **1500**| 
|:---|---:|---:|---:| ---: | ---: | 
| プールあたりの付属ストレージ (GB) | 250 | 500 | 750 | 1024 | 1536 | 
| プールあたりの選択可能な最大ストレージ容量 (GB)* | 250、500、750、1024 | 500、750、1024 | 750、1024 | 1024 | 1536 |
| プールあたりの最大インメモリ OLTP ストレージ容量 (GB) | 1 | 2 | 4 | 10 | 12 | 
| プールあたりの最大 DB 数 | 50 | 100 | 100 | 100 | 100 | 
| プールあたりの最大同時実行ワーカー (要求) 数 | 200 | 400 | 800 | 1600 | 2400 | 
| プールあたりの最大同時ログイン数 | 200 | 400 | 800 | 1600 | 2400 |
| プールあたりの最大同時セッション数 | 30000 | 30000 | 30000 | 30000 | 30000 | 
| データベースあたりの最小 eDTU 数 | 0、25、50、75、125 | 0、25、50、75、125、250 | 0、25、50、75、125、250、500 | 0、25、50、75、125、250、500、1000 | 0、25、50、75、125、250、500、1000、1500 | 
| データベースあたりの最大 eDTU 数 | 25、50、75、125 | 25、50、75、125、250 | 25、50、75、125、250、500 | 25、50、75、125、250、500、1000 | 25、50、75、125、250、500、1000、1500 |
| データベースあたりの最大ストレージ (GB)* | 1024 | 1024 | 1024 | 1024 | 1024 | 
||||||||

### <a name="premium-elastic-pool-limits-continued"></a>Premium エラスティック プールの制限 (続き) 

| プールあたりの eDTU 数 | **2000** | **2500** | **3000** | **3500** | **4000**|
|:---|---:|---:|---:| ---: | ---: | 
| プールあたりの付属ストレージ (GB) | 2048 | 2560 | 3072 | 3548 | 4096 |
| プールあたりの選択可能な最大ストレージ容量 (GB)* | 2048 | 2560 | 3072 | 3548 | 4096|
| プールあたりの最大インメモリ OLTP ストレージ容量 (GB) | 16 | 20 | 24 | 28 | 32 |
| プールあたりの最大 DB 数 | 100 | 100 | 100 | 100 | 100 | 
| プールあたりの最大同時実行ワーカー (要求) 数 | 3200 | 4000 | 4800 | 5600 | 6400 |
| プールあたりの最大同時ログイン数 | 3200 | 4000 | 4800 | 5600 | 6400 |
| プールあたりの最大同時セッション数 | 30000 | 30000 | 30000 | 30000 | 30000 | 
| データベースあたりの選択可能な最小 eDTU 数 | 0、25、50、75、125、250、500、1000、1750 | 0、25、50、75、125、250、500、1000、1750 | 0、25、50、75、125、250、500、1000、1750 | 0、25、50、75、125、250、500、1000、1750 | 0、25、50、75、125、250、500、1000、1750、4000 | 
| データベースあたりの選択可能な最大 eDTU 数 | 25、50、75、125、250、500、1000、1750 | 25、50、75、125、250、500、1000、1750 | 25、50、75、125、250、500、1000、1750 | 25、50、75、125、250、500、1000、1750 | 25、50、75、125、250、500、1000、1750、4000 | 
| データベースあたりの最大ストレージ (GB)* | 1024 | 1024 | 1024 | 1024 | 1024 | 
||||||||

> [!IMPORTANT]
> \* 付属のストレージ容量を超えるストレージ サイズはプレビュー段階であり、追加料金が適用されます。 詳細については、[SQL Database の価格のページ](https://azure.microsoft.com/pricing/details/sql-database/)を参照してください。 付属のストレージ容量を超えるストレージ サイズはプレビュー段階であり、追加料金が適用されます。 詳細については、[SQL Database の価格のページ](https://azure.microsoft.com/pricing/details/sql-database/)を参照してください。
>
> \* Premium レベルでは現在、次のリージョンで 1 TB を超えるストレージが使用できます: オーストラリア東部、オーストラリア南東部、ブラジル南部、カナダ中部、カナダ東部、米国中部、フランス中部、ドイツ中部、東日本、西日本、韓国中部、米国中北部、北ヨーロッパ、米国中南部、東南アジア、英国南部、英国西部、米国東部 2、米国西部、米国政府バージニア、および西ヨーロッパ。 [P11 ～ P15 の現時点での制限](#single-database-limitations-of-p11-and-p15-when-the-maximum-size-greater-than-1-tb)に関するページを参照してください。  
>

エラスティック プールのすべての DTU が使用されている場合は、プール内の各データベースが、同量のリソースを受け取ってクエリを処理します。 SQL Database サービスは、コンピューティング時間を均等にすることで、データベース間におけるリソース共有の公平性を実現します。 それ以外の場合、エラスティック プールのリソース共有の公平性は、データベースあたりの DTU分が 0 以外の値に設定されているときに、リソース量に加えて各データベースに適用されることが保証されます。

### <a name="database-properties-for-pooled-databases"></a>プールされたデータベースのデータベース プロパティ

次の表では、プールされたデータベースのプロパティについて説明します。

| プロパティ | [説明] |
|:--- |:--- |
| データベースあたりの最大 eDTU 数 |プール内の他のデータベースによる使用状況に基づいて使用可能な場合にプール内の任意のデータベースが使用できる eDTU の最大数。 データベースごとの最大 eDTU は、データベースに対して保証されたリソースではありません。 これは、プール内のすべてのデータベースに適用されるグローバル設定です。 データベースのピーク使用率を処理するのに十分高いデータベースあたり最大 eDTU 数を設定します。 プールでは通常、ホットとコールドのデータベース使用パターンがあり、すべてのデータベースが同時に最大に使用されることはないため、ある程度高めに上限が設定されています。 たとえば、データベースごとの最大使用量が 20 eDTU で、プールの 100 データベースの 20% のみが同時に最大で使用されるものとします。 データベースあたりの eDTU 上限が 20 eDTU に設定されている場合は、プールを 5 倍に設定し、プールあたりの eDTU 数を 400 に設定しておいても問題はありません。 |
| データベースあたりの最小 eDTU 数 |プール内の任意のデータベースで保証される eDTU の最小数。 これは、プール内のすべてのデータベースに適用されるグローバル設定です。 データベースあたりの最小 eDTU は 0 に設定でき、これが既定値です。 このプロパティは、0 とデータベースあたりの平均 eDTU 使用率の間に設定されます。 プール内のデータベースの数とデータベースごとの最小 eDTU の積がプールごとの eDTU の値を超えることはできません。 たとえば、プールに 20 のデータベースがあり、データベースあたりの最小 eDTU を 10 に設定する場合は、プールあたりの eDTU 数を少なくとも 200 eDTU にする必要があります。 |
| データベースあたりの最大ストレージ容量 |プール内のデータベースに対してユーザーによって設定される最大データベース サイズ。 プールされたデータベースは割り当てられたプール ストレージを共有するので、データベースが到達できるサイズは、残りのプール ストレージとデータベース サイズのうち、どちらか小さい方に制限されます。 最大データベース サイズとはデータ ファイルの最大サイズのことであり、ログ ファイルによって使用される領域は含まれません。 |
|||
 
## <a name="elastic-pool-change-storage-size"></a>エラスティック プール: ストレージ サイズを変更する

- エラスティック プールの eDTU 価格には、追加コストなしで一定量のストレージが含まれます。 付属の容量を超える分のストレージについては、追加費用を払うことで、1 TB までは 250 GB 単位で、1 TB 以降は 256 GB 単位で、最大サイズ制限までプロビジョニングできます。 付属するストレージの量と最大サイズ制限については、「[エラスティック プール: ストレージ サイズとパフォーマンス レベル](#elastic-pool-storage-sizes-and-performance-levels)」をご覧ください。
- エラスティック プールの追加ストレージは、[Azure Portal](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-the-azure-portal)、[PowerShell](/powershell/module/azurerm.sql/set-azurermsqlelasticpool)、[Azure CLI](/cli/azure/sql/elastic-pool#az_sql_elastic_pool_update)、または [REST API](/rest/api/sql/elasticpools/update) を使ってサイズを最大に増やすことでプロビジョニングできます。
- エラスティック プールの追加ストレージの料金は、追加ストレージ量にサービス レベルの追加ストレージ単価を掛けて計算します。 追加ストレージの価格について詳しくは、「[SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)」をご覧ください。

## <a name="elastic-pool-change-edtus"></a>エラスティック プール: eDTU を変更する

[Azure Portal](sql-database-elastic-pool.md#manage-elastic-pools-and-databases-using-the-azure-portal)、[PowerShell](/powershell/module/azurerm.sql/set-azurermsqlelasticpool)、[Azure CLI](/cli/azure/sql/elastic-pool#az_sql_elastic_pool_update)、または [REST API](/rest/api/sql/elasticpools/update) を使って、リソースのニーズに基づいてエラスティック プールに使用可能なリソースを増減できます。

- プールの eDTU を再スケーリングするときは、データベースの接続が短時間失われます。 これは、(プールではなく) 単一データベースの DTU を再スケーリングするときと同じ動作です。 再スケーリング操作中にデータベース接続が失われる時間とその影響について詳しくは、「[単一データベース: DTU を変更する](#single-database-change-storage-size)」をご覧ください。 
- プールの eDTU の再スケーリングに要する時間は、プール内のすべてのデータベースで使われているストレージの総量よって異なる場合があります。 一般に、再スケーリングの待機時間の平均は 100 GB あたり 90 分以下です。 たとえば、プール内のすべてのデータベースで使用される領域の合計が 200 GB の場合、プールの再スケーリングにかかる想定待機時間は、3 時間以下になります。 Standard または Basic レベルでは場合により、使われている容量に関係なく、再スケーリングの待機時間が 5 分未満になることがあります。
- 一般に、データベースあたりの最小 eDTU またはデータベースあたりの最大 eDTU の変更に要する時間は、5 分以内です。
- プールの eDTU をダウンサイズするときは、プールで使われている領域が、ターゲットのサービス レベルとパフォーマンス レベルで許可されている最大サイズより小さい必要があります。
- プールの eDTU を再スケーリングするとき、(1) プールの最大ストレージ サイズがターゲット プールでサポートされていて、かつ、(2) 最大ストレージ サイズがターゲット プールに付属するストレージ量を超える場合、追加のストレージ コストが適用されます。 たとえば、最大サイズが 100 GB の 100 eDTU のStandard プールを、50 eDTU の Standard プールにダウンサイズすると、ターゲット プールは最大サイズの 100 GB をサポートしますが、付属するストレージ量は 50 GB だけなので、追加ストレージ コストがかかります。 したがって、追加ストレージ量は 100 GB – 50 GB = 50 GB になります。 追加ストレージの価格については、「[SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)」をご覧ください。 実際に使われる領域の量が付属のストレージの量より少ない場合、データベースの最大サイズを付属の量に減らすことで、この追加コストを回避できます。 

## <a name="what-is-the-maximum-number-of-servers-and-databases"></a>サーバーとデータベースの最大数

| 最大値 | 値 |
| :--- | :--- |
| サーバーあたりのデータベース数 | 5000 |
| サブスクリプションあたりのサービスの数 (リージョンあたり) | 20 |
|||

> [!IMPORTANT]
> データベースの数がサーバーあたりの制限に近づくと、次の状況が発生します。
> <br> •    マスター データベースに対して実行するクエリの待機時間が増えます。  これには、リソース使用率統計情報のビューも含まれます (sys.resource_stats など)。
> <br> •    サーバー内のデータベースの列挙を要する、管理操作やポータル ビュー ポイント表示の待機時間が長くなります。

## <a name="what-happens-when-database-and-elastic-pool-resource-limits-are-reached"></a>データベース リソースとエラスティック プール リソースが制限に達したときの影響

### <a name="compute-dtus-and-edtus"></a>コンピューティング (DTU と eDTU)

(DTU および eDTU によって測定された) データベース コンピューティングの使用率が高くなると、クエリの待機時間が増加し、タイムアウトすることさえあります。このような状況下では、クエリはサービスによってキューに格納されることがあり、リソースが空くと実行用のリソースを提供されます。
高いコンピューティング使用率が発生する場合、次のような軽減オプションがあります。

- データベースまたエラスティック プールのパフォーマンス レベルを上げて、より多くの DTU または eDTU をデータベースに提供します。 「[単一データベース: DTU を変更する](#single-database-change-dtus)」および「[エラスティック プール: eDTU を変更する](#elastic-pool-change-edtus)」をご覧ください。
- クエリを最適化して、各クエリのリソース使用率を引き下げます。 詳しくは、「[クエリの調整とヒント](sql-database-performance-guidance.md#query-tuning-and-hinting)」をご覧ください。

### <a name="storage"></a>Storage

使用済みのデータベース容量が最大サイズの上限に達すると、データのサイズが増えるデータベースの挿入および更新は失敗し、クライアントは[エラー メッセージ](sql-database-develop-error-messages.md)を受け取ります。 データベースの SELECTS と DELETES は引き続き成功します。

高い容量使用率が発生する場合、次のような軽減オプションがあります。

- データベースまたはエラスティック プールの最大サイズを増やすか、より多くの付属ストレージを得られるパフォーマンス レベルに変更します。 「[Azure SQL Database のリソース制限](sql-database-dtu-resource-limits.md)」を参照してください。
- データベースがエラスティック プール内にある場合は、もう 1 つの方法として、データベースをプールの外に移動し、ストレージ領域が他のデータベースと共有されないようにすることもできます。

### <a name="sessions-and-workers-requests"></a>セッションとワーカー (要求) 

セッションおよびワーカーの最大数は、サービス レベルとパフォーマンス レベル (DTU と eDTU) によって決まります。 セッションまたはワーカーが上限に達した場合、新しい要求は拒否され、クライアントはエラー メッセージを受け取ります。 利用可能な接続の数はアプリケーションで制御できますが、同時ワーカーの数は推定または制御が困難なことがよくあります。 データベース リソースが上限に達し、クエリを長時間実行したためにワーカーが滞留するピーク負荷期間は特にそうです。 

セッションまたはワーカーの使用率が高い場合は、次のような軽減オプションがあります。
- データベースまたはエラスティック プールのサービス レベルまたはパフォーマンス レベルを高くします。 「[単一データベース: ストレージ サイズを変更する](#single-database-change-storage-size)」、「[単一データベース: DTU を変更する](#single-database-change-dtus)」、「[エラスティック プール: ストレージ サイズを変更する](#elastic-pool-change-storage-size)」、「[エラスティック プール: eDTU を変更する](#elastic-pool-change-edtus)」をご覧ください。
- ワーカー使用率上昇の原因がコンピューティング リソースの競合である場合は、クエリを最適化して各クエリのリソース使用率を下げます。 詳しくは、「[クエリの調整とヒント](sql-database-performance-guidance.md#query-tuning-and-hinting)」をご覧ください。

## <a name="next-steps"></a>次の手順

- よく寄せられる質問の回答については、「[SQL Database に関する FAQ](sql-database-faq.md)」を参照してください。
- Azure の一般的な制限については、「[Azure サブスクリプションとサービスの制限、クォータ、制約](../azure-subscription-service-limits.md)」をご覧ください。
- DTU と eDTU については、「[データベース トランザクション ユニット (DTU) とエラスティック データベース トランザクション ユニット (eDTU) の説明](sql-database-what-is-a-dtu.md)」をご覧ください。
- tempdb のサイズ制限については、https://docs.microsoft.com/sql/relational-databases/databases/tempdb-database#tempdb-database-in-sql-database を参照してください。
