---
title: Como adicionar ou remover namespaces importados (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 015f2efa352b5ff2d8b87e356972270c175d0168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Como adicionar ou remover namespaces importados (Visual Basic)
Importar um namespace permite que você use elementos deste namespace em seu código sem qualificar totalmente o elemento. Por exemplo, se quiser acessar o método `Create` na classe `System.Messaging.MessageQueue`, você pode importar o namespace `System.Messaging` e apenas se referir ao elemento necessário em código como `MessageQueue.Create`.  

 Namespaces importados são gerenciados na página **Referências** do **Designer de Projeto**. As importações que você especificar na caixa de diálogo são passadas diretamente ao compilador (`/imports`) e se aplicam a todos os arquivos em seu projeto. Use a demonstrativo `Imports` para utilizar um namespace em um arquivo de código-fonte único.  

### <a name="to-add-an-imported-namespace"></a>Para adicionar um namespace importado  

1.  No **Gerenciador de Soluções**, clique duas vezes no nó **Meu Projeto** do projeto.  

2.  No **Designer de Projeto**, clique na guia **Referências**.  

3.  Na lista **Namespaces Importados**, marque a caixa de seleção do namespace que você deseja adicionar.  

    > [!NOTE]
    >  Para ser importado, o namespace deve estar em um componente referenciado. Se o namespace não aparecer na lista, você precisará adicionar uma referência ao componente que o contém. Para obter mais informações, consulte [Gerenciando referências em um projeto](managing-references-in-a-project.md).  
  
### <a name="to-remove-an-imported-namespace"></a>Para remover um namespace importado  

1.  No **Gerenciador de Soluções**, clique duas vezes no nó **Meu Projeto** do projeto.  

2.  No **Designer de Projeto**, clique na guia **Referências**.  

3.  Na lista **Namespaces Importados**, desmarque a caixa de seleção do namespace que você deseja remover.  

## <a name="user-imports"></a>Importações de usuário  
 Importações de usuário permitem importar uma classe específica dentro de um namespace, em vez de todo o namespace. Por exemplo, seu aplicativo pode ter uma importação para o namespace `Systems.Diagnostics`, mas a única classe dentro do namespace em que você tem interesse é a classe `Debug`. Você pode definir `System.Diagnostics.Debug` como uma importação de usuário e, em seguida, remover a importação de `System.Diagnostics`.  

 Se posteriormente mudar de ideia e decidir que realmente precisava da classe `EventLog`, você pode inserir `System.Diagnostics.EventLog` como uma importação de usuário e substituir `System.Diagnostics.Debug` usando a funcionalidade de atualização.  

#### <a name="to-add-a-user-import"></a>Para adicionar uma importação de usuário  

1.  No **Gerenciador de Soluções**, clique duas vezes no nó **Meu Projeto** do projeto.  

2.  No **Designer de Projeto**, clique na guia **Referências**.  

3.  Na caixa de texto abaixo da lista **Namespaces Importados**, digite o nome completo do namespace que deseja importar, incluindo o namespace raiz.  

4.  Clique no botão **Adicionar importação de usuário** para adicionar o namespace à lista **Namespaces importados**.  

    > [!NOTE]
    >  O botão **Adicionar importação de usuário** será desabilitado se o namespace corresponder a um que já está na lista; não é possível adicionar uma importação duas vezes.  

#### <a name="to-update-a-user-import"></a>Para atualizar uma importação de usuário  

1.  No **Gerenciador de Soluções**, clique duas vezes no nó **Meu Projeto** do projeto.  

2.  No **Designer de Projeto**, clique na guia **Referências**.  

3.  Na lista **Namespaces Importados**, selecione o namespace que você deseja alterar.  

4.  Na caixa de texto abaixo da lista de **Namespaces Importados**, digite o nome do novo namespace.  

5.  Clique no botão **Adicionar importação de usuário** para atualizar o namespace na lista **Namespaces importados**.  

## <a name="see-also"></a>Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)
