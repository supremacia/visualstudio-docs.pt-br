---
title: 'Como: imprimir documentos do Visio programaticamente | Microsoft Docs'
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Como imprimir documentos do Visio programaticamente
  Você pode imprimir um documento do Microsoft Office Visio completo ou apenas uma página específica.  
  
 Para obter detalhes sobre os métodos de impressão, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) método e [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) método .  
  
## <a name="printing-a-visio-document"></a>Imprimir um documento do Visio  
  
#### <a name="to-print-a-complete-document"></a>Para imprimir um documento completo  
  
-   Chame o método Microsoft.Office.Interop.Visio.Document.Print do objeto Microsoft.Office.Interop.Visio.Document que você deseja imprimir.  
  
     O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Imprimir uma página de um documento do Visio  
  
#### <a name="to-print-a-page-of-a-document"></a>Para imprimir uma página de um documento  
  
-   Chame o método Microsoft.Office.Interop.Visio.Pages.Print do objeto Microsoft.Office.Interop.Visio.Pages que você deseja imprimir.  
  
     O exemplo de código a seguir imprime a primeira página do documento ativo. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Como: criar novos documentos do Visio programaticamente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Como: abrir documentos do Visio programaticamente](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Como: fechar documentos do Visio programaticamente](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Como salvar documentos do Visio de forma programática](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  