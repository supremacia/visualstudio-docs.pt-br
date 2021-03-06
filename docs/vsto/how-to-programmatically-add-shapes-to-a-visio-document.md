---
title: 'Como: adicionar formas a um documento do Visio programaticamente | Microsoft Docs'
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
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d73c59ac9ba89a5814a264bb8e8fe3c83b9789e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Como adicionar formas a um documento do Visio programaticamente
  Você pode adicionar formas para um documento do Microsoft Office Visio recuperando os mestres de um estêncil e descartando as formas na página ativa.  
  
 Para obter mais informações, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) método [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) propriedade e [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) método.  
  
## <a name="adding-shapes-to-a-visio-document"></a>Adicionando formas para um documento do Visio  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>Adicionar formas a um documento do Visio  
  
-   Com um documento ativo, recuperar os mestres de coleção Documents.Masters e descartar as formas no documento ativo. Você pode recuperar um mestre usando o índice ou o nome do mestre.  
  
     O exemplo de código a seguir cria um documento em branco do Visio e, em seguida, abre-o com o **formas básicas** estêncil encaixado. O código recupera várias formas e descarta-los na página ativa.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Soluções do Visio](../vsto/visio-solutions.md)   
 [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)   
 [Trabalhando com formas do Visio](../vsto/working-with-visio-shapes.md)   
 [Como copiar e colar formas em um documento do Visio de forma programática](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  