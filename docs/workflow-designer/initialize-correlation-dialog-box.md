---
title: "Inicializar a caixa de diálogo correlação | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 641526a0577c74ff590d701560e5266c85fa60dc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar a caixa de diálogo correlação

O **inicializar correlação** no Designer de fluxo de trabalho do Windows, a caixa de diálogo é usada para editar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade de um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. Para obter mais informações, consulte o [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) tópico.

 A tabela a seguir descreve os elementos de interface de usuário do **inicializar correlação** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Correlação**|<xref:System.ServiceModel.Activities.CorrelationHandle> de correlação para inicializar.|
|**Inicializar**|Um par chave/valor que contém os dados para inicializar. Isso corresponde à propriedade de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Um exemplo de um par chave/valor válido deve ser uma chave chamada "OrderID" emparelhado com uma variável chamada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar a caixa de diálogo correlação inicializar

-   Clique em **exibição** no **InitializeCorrelation** atividade designer ou selecione um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] e, em seguida, clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade no a grade de propriedade.

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)