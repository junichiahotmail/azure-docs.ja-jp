---
title: PowerShell でゾーン冗長パブリック IP アドレス フロントエンドを使用してパブリック Load Balancer Standard を作成する | Microsoft Docs
description: PowerShell でゾーン冗長パブリック IP アドレス フロントエンドを使用してパブリック Load Balancer Standard を作成する方法について説明します。
services: load-balancer
documentationcenter: na
author: KumudD
manager: timlt
editor: ''
tags: azure-resource-manager
ms.assetid: ''
ms.service: load-balancer
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 03/23/2018
ms.author: kumud
ms.openlocfilehash: d9f890eba85900d7be8aa37da8c86c0ec2e424f0
ms.sourcegitcommit: 20d103fb8658b29b48115782fe01f76239b240aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
#  <a name="create-a-public-load-balancer-standard-with-zone-redundant-public-ip-address-frontend-using-powershell"></a>PowerShell でゾーン冗長パブリック IP アドレス フロントエンドを使用してパブリック Load Balancer Standard を作成する

この記事では、パブリック IP Standard アドレスでゾーン冗長フロントエンドを使用してパブリック [Load Balancer Standard](https://aka.ms/azureloadbalancerstandard) を作成する手順について説明します。

Azure サブスクリプションをお持ちでない場合は、開始する前に [無料アカウント](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) を作成してください。

> [!NOTE]
 可用性ゾーンのサポートは、Azure リソース、リージョン、および VM サイズ ファミリを選択するために使用できます。 使用を開始する方法、および可用性ゾーンを試行する場合にどの Azure リソース、リージョン、および VM サイズ ファミリを使用できるかの詳細については、「[Overview of Availability Zones (可用性ゾーンの概要)](https://docs.microsoft.com/azure/availability-zones/az-overview)」を参照してください。 サポートについては、[StackOverflow](https://stackoverflow.com/questions/tagged/azure-availability-zones) でアクセスするか、または [Azure サポート チケットを開く](../azure-supportability/how-to-create-azure-support-request.md?toc=%2fazure%2fvirtual-network%2ftoc.json)ことができます。

## <a name="log-in-to-azure"></a>Azure にログインする

`Login-AzureRmAccount` コマンドで Azure サブスクリプションにログインし、画面上の指示に従います。

```powershell
Login-AzureRmAccount
```

## <a name="create-resource-group"></a>Create resource group

リソース グループを作成するには、次のコマンドを使用します。

```powershell
New-AzureRmResourceGroup -Name myResourceGroup -Location westeurope
```

## <a name="create-a-public-ip-standard"></a>パブリック IP Standard の作成 
パブリック IP Standard を作成するには、次のコマンドを使用します。

```powershell
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName myResourceGroup -Name 'myPublicIP' `
  -Location westeurope -AllocationMethod Static -Sku Standard 
```

## <a name="create-a-front-end-ip-configuration-for-the-website"></a>Web サイトのフロントエンド IP 構成の作成

フロントエンド IP 構成を作成するには、次のコマンドを使用します。

```powershell
$feip = New-AzureRmLoadBalancerFrontendIpConfig -Name 'myFrontEndPool' -PublicIpAddress $publicIp
```

## <a name="create-the-back-end-address-pool"></a>バックエンド アドレス プールの作成

バックエンド アドレス プールを作成するには、次のコマンドを使用します。

```powershell
$bepool = New-AzureRmLoadBalancerBackendAddressPoolConfig -Name 'myBackEndPool'
```

## <a name="create-a-load-balancer-probe-on-port-80"></a>ポート 80 でのロード バランサー プローブの作成

ポート 80 でロード バランサーの正常性プローブを作成するには、次のコマンドを使用します。

```powershell
$probe = New-AzureRmLoadBalancerProbeConfig -Name 'myHealthProbe' -Protocol Http -Port 80 `
  -RequestPath / -IntervalInSeconds 360 -ProbeCount 5
```

## <a name="create-a-load-balancer-rule"></a>ロード バランサー規則の作成
 ロード バランサー ルールを作成するには、次のコマンドを使用します。

```powershell
   $rule = New-AzureRmLoadBalancerRuleConfig -Name HTTP -FrontendIpConfiguration $feip -BackendAddressPool  $bepool -Probe $probe -Protocol Tcp -FrontendPort 80 -BackendPort 80
```

## <a name="create-a-load-balancer"></a>ロード バランサーの作成
Load Balancer Standard を作成するには、次のコマンドを使用します。

```powershell
$lb = New-AzureRmLoadBalancer -ResourceGroupName myResourceGroup -Name 'MyLoadBalancer' -Location westeurope `
  -FrontendIpConfiguration $feip -BackendAddressPool $bepool `
  -Probe $probe -LoadBalancingRule $rule -Sku Standard
```

## <a name="next-steps"></a>次の手順
- [Standard Load Balancer と可用性ゾーン](load-balancer-standard-availability-zones.md)を確認します。



