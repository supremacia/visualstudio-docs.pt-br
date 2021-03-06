---
title: "Como: adicionar texto e formatação a células em tabelas do Word programaticamente | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2742215f01065fb90d8a312eaa324e0cecccb57b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Como adicionar texto e formatação a células em tabelas do Word programaticamente
  Cada tabela consiste em uma coleção de células. Cada indivíduo <xref:Microsoft.Office.Interop.Word.Cell> objeto representa uma célula na tabela. Você se referir a cada célula por sua localização na tabela. Este exemplo refere-se à célula localizada na primeira linha e a primeira coluna da tabela; adiciona texto à célula; e aplica formatação.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Para adicionar texto e formatação a células  
  
1.  Fazer referência à célula por sua localização na tabela, adicionar texto à célula e aplique a formatação.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento. Para usar este exemplo, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo. Para usar o exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar programaticamente tabelas do Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Como: adicionar programaticamente as linhas e colunas a tabelas do Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Como preencher tabelas do Word com propriedades do documento de forma programática](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  