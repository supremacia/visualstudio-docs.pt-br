---
title: "Como: exibir programaticamente os comentários da planilha | Microsoft Docs"
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
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c43e33030cffc78bc8ee4a0665c9334bc6e8bca7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Como exibir comentários em planilhas programaticamente
  Programaticamente, você pode mostrar e ocultar os comentários em planilhas do Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Para exibir todos os comentários em uma planilha em uma personalização no nível do documento  
  
1.  Definir o <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> propriedade **true** se você deseja mostrar comentários; caso contrário, **false**. Esse código deve ser colocado em uma classe de folha, não o `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Para exibir todos os comentários em uma planilha em um suplemento do VSTO do nível do aplicativo  
  
1.  Definir o <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> propriedade **true** se você deseja mostrar comentários; caso contrário, **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: adicionar programaticamente e excluir os comentários da planilha](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  