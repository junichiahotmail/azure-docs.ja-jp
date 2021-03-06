---
title: '手順 6: Machine Learning Web サービスにアクセスする | Microsoft Docs'
description: 予測ソリューションの開発に関するチュートリアルの中の、アクティブな Azure Machine Learning Web サービスにアクセスするステップの 6 番目の手順です。
services: machine-learning
documentationcenter: ''
author: YasinMSFT
ms.author: yahajiza
manager: hjerez
editor: cgronlun
ms.assetid: 6a65c89a-40ab-4673-8dd8-8eee0a150e3b
ms.service: machine-learning
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/23/2017
ms.openlocfilehash: 82e068ca3656b28e5e8dad19a31d6e5ff9c6f8b6
ms.sourcegitcommit: 48ab1b6526ce290316b9da4d18de00c77526a541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="walkthrough-step-6-access-the-azure-machine-learning-web-service"></a>チュートリアル手順 6: Azure Machine Learning Web サービスにアクセスする

これは、「 [チュートリアル: 信用リスク評価のための予測分析ソリューションを Azure Machine Learning で開発する](walkthrough-develop-predictive-solution.md)

1. [Machine Learning ワークスペースの作成](walkthrough-1-create-ml-workspace.md)
2. [既存のデータをアップロードする](walkthrough-2-upload-data.md)
3. [新しい実験を作成する](walkthrough-3-create-new-experiment.md)
4. [モデルをトレーニングして評価する](walkthrough-4-train-and-evaluate-models.md)
5. [Web サービスをデプロイする](walkthrough-5-publish-web-service.md)
6. **Web サービスにアクセスする**

- - -
このチュートリアルで前の手順では、信用リスク予測モデルを使用する Web サービスをデプロイしました。 これにより、ユーザーは、Web サービスにデータを送信し、結果を受信できます。 

Web サービスは、次の 2 つの方法のいずれかで、REST API を使用してデータを受信して返すことができる Azure Web サービスです。  

* **要求/応答** - ユーザーが HTTP プロトコルを使用して 1 行以上のクレジット データをサービスに送信し、サービスが 1 つ以上の結果のセットを返します。
* **バッチ実行** - ユーザーが Azure BLOB に 1 行以上のクレジット データを格納し、そのBLOB の場所をサービスに送信します。 サービスは、入力 BLOB 内のデータのすべての行にスコアを付け、結果を別の BLOB に格納し、この BLOB のURL を返します。  

従来の Web サービスにアクセスする最も迅速で簡単な方法は、[Azure ML 要求応答サービス Web アプリ](https://azure.microsoft.com/marketplace/partners/microsoft/azuremlaspnettemplateforrrs/)または[Azure ML バッチ実行サービス Web アプリ テンプレート](https://azure.microsoft.com/marketplace/partners/microsoft/azuremlbeswebapptemplate/)を使用することです。

このような Web アプリ テンプレートを使用すると、Web サービスの入力データとサービスで返される内容を認識するカスタム Web アプリを構築できます。 必要な操作は、Web サービスおよびデータへのアクセスを許可することだけで、後の処理はテンプレートによって行われます。

Web アプリ テンプレートの使用方法の詳細については、「[Web アプリケーション テンプレートによる Azure Machine Learning Web サービスの使用](consume-web-service-with-web-app-template.md)」をご覧ください。

R、C#、Python プログラミング言語で提供されるスターター コードを使用して、Web サービスにアクセスするカスタム アプリケーションを開発することもできます。

詳細については、「[Machine Learning の実験からデプロイされた Azure Machine Learning Web サービスを使用する方法](consume-web-services.md)」を参照してください。

