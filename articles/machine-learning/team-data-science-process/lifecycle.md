---
title: Team Data Science Process ライフサイクル - Azure | Microsoft Docs
description: データ サイエンス プロジェクトを実行するために必要な手順について説明します
services: machine-learning
documentationcenter: ''
author: bradsev
manager: cgronlun
editor: cgronlun
ms.assetid: b1f677bb-eef5-4acb-9b3b-8a5819fb0e78
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/04/2017
ms.author: bradsev
ms.openlocfilehash: a971e40bc4338f187991eeae991044248844d8b6
ms.sourcegitcommit: d74657d1926467210454f58970c45b2fd3ca088d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="the-team-data-science-process-lifecycle"></a>Team Data Science Process ライフサイクル

Team Data Science Process (TDSP) には、データ サイエンス プロジェクトを体系化するために使用できる推奨ライフサイクルが用意されています。 このライフサイクルは、プロジェクトを実行する際に、その開始から終了までにわたって進められる通常のステップを大まかにまとめたものです。 [CRISP-DM](https://wikipedia.org/wiki/Cross_Industry_Standard_Process_for_Data_Mining) (Cross Industry Standard Process for Data Mining) や [KDD](https://wikipedia.org/wiki/Data_mining#Process) (Knowledge Discovery in Databases) などのデータ サイエンス ライフサイクルや組織独自のカスタム プロセスを使用する場合でも、このタスク ベースの TDSP を使用できます。 

このライフサイクルは、インテリジェント アプリケーションに付属することを意図したデータ サイエンス プロジェクト向けに設計されています。 このようなアプリケーションでは、機械学習モデルや人工知能モデルをデプロイして予測分析に使用します。 このプロセスは、探索的データ サイエンス プロジェクトや、アドホック分析プロジェクトに利用しても効果的ですが、 それらのプロジェクトでは、ここで説明する手順のいくつかは必要ない場合があります。 

TDSP ライフサイクルは、繰り返し実行される 5 つの主なステージで構成されています。 次の段階があります。

   1. [ビジネスの把握](lifecycle-business-understanding.md)
   2. [データの取得と理解](lifecycle-data.md)
   3. [モデリング](lifecycle-modeling.md)
   4. [デプロイ](lifecycle-deployment.md)
   5. [顧客による受け入れ](lifecycle-acceptance.md)

TDSP ライフサイクルを視覚化すると、次のようになります。 

![TDSP ライフサイクル](./media/lifecycle/tdsp-lifecycle2.png) 


TDSP ライフサイクルは、繰り返し行う一連のステップとしてモデル化されており、予測モデルを使用するために必要なタスクのガイダンスとして役立ちます。 インテリジェント アプリケーションを構築するために使用する予定の運用環境に予測モデルをデプロイします。 このプロセス ライフサイクルのゴールは、データ サイエンス プロジェクトを契約上の明確な終着点へと継続的に導くことです。 データ サイエンスは、調査と発見の繰り返しです。 標準化されたテンプレートを使用した適切に定義された一連の成果物を使用してチームと顧客にタスクを伝達できることは、誤解を避けるために役立ちます。 これらのテンプレートを使用すると、複雑なデータ サイエンス プロジェクトが正常に完了する可能性も増加します。

各ステージで、以下のような情報を提供します。

   * **目標**: 具体的な目標。
   * **実行方法**: 特定のタスクの概要とそれらを完了する方法についてのガイダンス。
   * **アーティファクト**: 成果物と、それらを作成するためのサポート。

## <a name="next-steps"></a>次の手順

特定のシナリオ のプロセスに伴うすべての手順を初めから終わりまで完全に説明するチュートリアルが用意されています。 [例を含むチュートリアル](walkthroughs.md)の記事に、各シナリオが、簡潔な説明とリンク付きで示されています。 これらのチュートリアルは、クラウドとオンプレミスのツールおよびサービスをワークフローまたはパイプラインに組み込んで、インテリジェントなアプリケーションを作成する方法について説明しています。 

Azure Machine Learning Studio を使用して TDSP の手順を実行する方法の例については、「[Azure Machine Learning での Team Data Science Process の使用](http://aka.ms/datascienceprocess)」を参照してください。
