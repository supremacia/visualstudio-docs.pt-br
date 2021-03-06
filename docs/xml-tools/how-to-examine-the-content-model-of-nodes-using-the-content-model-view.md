---
title: "Como: Examine o modelo de conteúdo de nós usando a exibição do modelo de conteúdo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4856554b92f5689e17141004b7d4e0ffe5e781cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Como: Examine o modelo de conteúdo de nós usando a exibição do modelo de conteúdo
Este tópico descreve como explorar os nós usando o [exibição do modelo de conteúdo](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para criar um novo arquivo XSD e exibir o elemento raiz no modo do modelo de conteúdo  
  
1.  Crie um novo arquivo de esquema XML.  
  
2.  Clique em **Use o Editor de XML para exibir e editar o arquivo de esquema XML subjacente** no modo de exibição de iniciar.  
  
3.  Copie o código de exemplo de esquema XML de [esquema XML de exemplo: esquema de ordem de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) e cole-o para substituir o código que foi adicionado para o novo arquivo XSD por padrão.  
  
4.  Selecione o `purchaseOrder` elemento no Gerenciador de esquema clicando com o `purchaseOrder` elemento no Editor de XML e selecionando **Mostrar no Gerenciador de XML**.  
  
5.  Clique com botão direito do `purchaseOrder` no Gerenciador de XML e selecione **Mostrar na exibição do modelo de conteúdo**.  
  
     A exibição do modelo de conteúdo exibe o elemento de `purchaseOrder` na superfície de design.  
  
6.  Expanda `shipTo`, `billTo`, e nós de `items` clicando duas vezes em cada nó ou double clicando na seta à direita de cada nó.  
  
     Os nós de elemento de `purchaseOrder` são expandidos e agora você pode ver o modelo de conteúdo do elemento.  
  
7.  Clique em qualquer nó no elemento de `purchaseOrder` e examine a barra de rastreamento para ver onde o esquema define o nó selecionado for encontrado.  
  
8.  Clique o **Mostrar documentação** botão na barra de ferramentas para alternar documentação XSD. Você também pode clicar com o botão direito do mouse na superfície de design para ativar /desativar a documentação.  
  
9. Clique o `purchaseOrder` nó e selecione **gerar XML de exemplo** para ver o documento de instância XML.