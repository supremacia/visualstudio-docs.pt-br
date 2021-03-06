---
title: "Como: adicionar partes XML a personalizações no nível do documento | Microsoft Docs"
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
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27e50ed67cadd011f3b56c21e5528b870bbcb3c2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Como adicionar partes XML a personalizações no nível do documento
  Você pode armazenar dados XML em uma pasta de trabalho do Microsoft Office Excel ou um documento do Microsoft Office Word, criando uma parte XML personalizada em uma personalização no nível do documento. Para obter mais informações, consulte [visão geral de partes de XML personalizado](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio não oferecem projetos no nível de documento do Microsoft Office PowerPoint. Para obter informações sobre como adicionar uma parte XML personalizada para uma apresentação do PowerPoint usando um suplemento do VSTO, consulte [como: adicionar partes XML a documentos pelo uso de suplementos do VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Para adicionar uma parte XML personalizada a uma pasta de trabalho do Excel  
  
1.  Adicionar um novo <xref:Microsoft.Office.Core.CustomXMLPart> o objeto para o <xref:Microsoft.Office.Core.CustomXMLParts> coleção na pasta de trabalho. O <xref:Microsoft.Office.Core.CustomXMLPart> contém a cadeia de caracteres XML que você deseja armazenar na pasta de trabalho.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]  
  
2.  Adicionar o `AddCustomXmlPartToWorkbook` método para o `ThisWorkbook` classe em um projeto de nível de documento para Excel.  
  
3.  Chame o método de outro código no seu projeto. Por exemplo, para criar a parte XML personalizada quando o usuário abre a pasta de trabalho, chame o método do `ThisWorkbook_Startup` manipulador de eventos.  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Para adicionar uma parte XML personalizada para um documento do Word  
  
1.  Adicionar um novo <xref:Microsoft.Office.Core.CustomXMLPart> o objeto para o <xref:Microsoft.Office.Core.CustomXMLParts> coleção no documento. O <xref:Microsoft.Office.Core.CustomXMLPart> contém a cadeia de caracteres XML que você deseja armazenar no documento.  
  
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]  
  
2.  Adicionar o `AddCustomXmlPartToDocument` método para o `ThisDocument` classe em um projeto de nível de documento para Word.  
  
3.  Chame o método de outro código no seu projeto. Por exemplo, para criar a parte XML personalizada quando o usuário abre o documento, chame o método do `ThisDocument_Startup` manipulador de eventos.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para simplificar, este exemplo usa uma cadeia de caracteres XML que é definida como uma variável local no método. Normalmente, você deverá obter o XML de uma fonte externa, como um arquivo ou um banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md)   
 [Como adicionar partes XML personalizadas aos documentos usando suplementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  