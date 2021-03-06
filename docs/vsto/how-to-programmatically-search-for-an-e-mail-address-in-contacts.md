---
title: "Como: procurar um endereço de email em contatos programaticamente | Microsoft Docs"
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d9ab451d433536c7ebf5931aa2c971b08ed5c09b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Como procurar um endereço de email em Contatos programaticamente
  Este exemplo procura uma pasta de contato para contatos que têm o nome de domínio **example.com** em seus endereços de email.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Contatos que têm o nome de domínio **example.com** em seus endereços de email (por exemplo, `somebody@example.com`), e que têm nomes e sobrenomes.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com itens de contato](../vsto/working-with-contact-items.md)   
 [Como: enviar email](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Como: acessar programaticamente os contatos do Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Como adicionar uma entrada a contatos do Outlook de forma programática](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  