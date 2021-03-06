---
title: '&lt;Agendas&gt; elemento (Bootstrapper) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: b7924515dbb661a4281397817be4b1b68487a6ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Agendas&gt; elemento (Bootstrapper)
O `Schedules` elemento contém `Schedule` elementos, que definem a horários específicos em quais comandos definidos pelo `Command` elemento deve ser executado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `Schedules` elemento é um filho de `Product` elemento. Cada `Product` elemento pode ter no máximo uma `Schedules` elemento. O `Schedules` elemento não tem atributos.  
  
## <a name="schedule"></a>Agendamento  
 O `Schedule` elemento é um filho de `Schedules` elemento. Um `Schedules` elemento deve ter pelo menos um `Schedule` elemento.  
  
 `Schedule`tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O nome do item de agenda. Isso corresponde ao `ScheduleName` propriedade o `Command` elemento. Quando um `Command` faz referência a agenda nomeada, ela será executada somente no período indicado pelo `Schedule` elemento. Agendas também podem ser associadas a `FailIf` e `BypassIf` elementos, que restringem esses testes condicionais para a execução da agenda especificada. Para obter mais informações, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 Um determinado `Schedule` elemento pode ter exatamente um dos seguintes filhos.  
  
## <a name="buildlist"></a>BuildList  
 O `BuildList` elemento instrui o instalador para executar um comando imediatamente depois que o aplicativo de inicialização é iniciado.  
  
## <a name="beforepackage"></a>BeforePackage  
 O `BeforePackage` elemento instrui o instalador para executar um comando antes de instalar o pacote especificado.  
  
## <a name="afterpackage"></a>AfterPackage  
 O `AfterPackage` elemento instrui o instalador para executar um comando depois de instalar o pacote especificado.  
  
## <a name="see-also"></a>Consulte também  
 [\<Produto > elemento](../deployment/product-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)