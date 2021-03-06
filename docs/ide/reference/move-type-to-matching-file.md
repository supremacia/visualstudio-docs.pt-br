---
title: "Refatoração Mover tipo para arquivo correspondente no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 87619c7938afdf92da6ca1b03c3090ad7d72834c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refatoração Mover um tipo para um arquivo correspondente

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite mover o tipo selecionado para um arquivo separado com o mesmo nome.

**Quando:** você tem várias classes, structs, interfaces, etc. no mesmo arquivo que deseja separar.

**Por quê:** colocar vários tipos no mesmo arquivo pode dificultar a localização desses tipos. Ao mover os tipos de arquivos com o mesmo nome, o código torna-se mais legível e mais fácil de navegar.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro do nome do tipo para mover:

   - C#:

    ![Código realçado – C#](media/movetype-highlight-cs.png)

   - Visual Basic:

    ![Código realçado – Visual Basic](media/movetype-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover o tipo para *TypeName*.cs** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.
   - **Mouse**
     - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Mover o tipo para *TypeName*.cs** no pop-up da janela Visualização onde *TypeName* é o nome do tipo selecionado.

   O tipo é movido para um novo arquivo com esse nome, como parte da sua solução.

   - C#:

    ![Resultado embutido – C#](media/movetype-result-cs.png)

   - Visual Basic:

    ![Resultado embutido – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)