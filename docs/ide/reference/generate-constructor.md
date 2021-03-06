---
title: Gerar um construtor no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 0767b47fcf4456e1ac198674ece6c9de31850279
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="generate-a-constructor-in-visual-studio"></a>Gerar um construtor no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código para um novo construtor em uma classe.

**Quando:** você introduz um novo construtor e deseja declará-lo corretamente automaticamente, ou modifica um construtor existente.

**Por quê:** você poderia declarar o construtor antes de usá-lo; no entanto, esse recurso o gerará automaticamente com os parâmetros apropriados. Além disso, modificar um construtor existente exige a atualização de todos os callsites, a menos que você use este recurso para atualizá-los automaticamente.

**Como:** há várias maneiras de gerar um construtor:

   - [Gerar construtor e selecionar membros](#pick)
   - [Gerar construtor desde campos selecionados](#selection)
   - [Gerar construtor desde uma nova utilização](#usage)
   - [Adicionar o parâmetro ao construtor existente](#addparameter)
   - [Criar e inicializar o campo/propriedade de um parâmetro de construtor](#create)

## <a id = "pick"></a> Gerar construtor e selecionar membros (somente C#)

1. Coloque o cursor em qualquer linha vazia em uma classe:

   ![Cursor em linha vazia](media/constructor1-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha vazia na classe.

   ![Visualização da geração do construtor](media/constructor1-preview-cs.png)

1. Selecione **Gerar construtor...** no menu suspenso.

   A caixa de diálogo **Selecionar membros** é aberta.

1. Selecione os membros que você deseja incluir como parâmetros do construtor. Você pode ordená-los usando as setas para cima e para baixo. Escolha **OK**.

   ![Caixa de diálogo Escolher membros](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Você pode marcar a caixa de diálogo **Adicionar verificações nulas** para gerar automaticamente verificações nulas para os parâmetros do construtor.

   O construtor é criado com os parâmetros especificados.

   ![Resultado da geração do construtor](media/constructor1-result-cs.png)

## <a id="selection"></a> Gerar construtor usando campos selecionados (somente C#)

1. Realce os membros que você deseja inserir no construtor gerado:

   ![Realçar membros](media/constructor2-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com a seleção.

     ![Visualização da geração do construtor](media/constructor2-preview-cs.png)

1. Selecione **Gerar construtor 'TypeName(...)'** no menu suspenso.

   O construtor é criado com os parâmetros selecionados.

   ![Resultados da ação de gerar construtor](media/constructor2-result-cs.png)

## <a id="usage"></a> Gerar construtor de uso novo (C# e Visual Basic)

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica uma chamada para um construtor que ainda não existe.

   - C#:

    ![Código em C# realçado](media/constructor-highlight-cs.png)

   - Visual Basic:

    ![Código em VB realçado](media/constructor-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

    ![Visualização da geração do construtor](media/constructor-preview-cs.png)

1. Selecione **Gerar construtor em '*TypeName*'** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O construtor é criado, com os parâmetros inferidos com base em seu uso.

   - C#:

      ![Gerar o resultado do método C#](media/constructor-result-cs.png)

   - Visual Basic:

      ![Gerar o resultado do método VB](media/constructor-result-vb.png)

## <a id="addparameter"></a> Adicionar parâmetro ao construtor existente (somente C#)

1. Adicione um parâmetro a uma chamada de construtor existente.

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um construtor que ainda não existe.

    ![Realce da geração do construtor](media/constructor4-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

    ![Visualização da geração do construtor](media/constructor4-preview-cs.png)

1. Selecione **Adicionar parâmetro em 'TypeName(...)'** no menu suspenso.

   O parâmetro é adicionado ao construtor, com o tipo inferido com base em seu uso.

   ![Resultado da geração do construtor](media/constructor4-result-cs.png)

## <a id="create"></a> Criar e inicializar um campo ou uma propriedade de um parâmetro de construtor (somente C#)

1. Localize um construtor existente e adicione um parâmetro:

   ![Realce da geração do construtor](media/constructor5-highlight-cs.png)

1. Coloque o cursor dentro do parâmetro recém-adicionado.

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o parâmetro adicionado.

   ![Visualização da geração do construtor](media/constructor5-preview-cs.png)

1. Selecione **Criar e inicializar propriedade** ou **Criar e inicializar campo** no menu suspenso.

   O campo ou a propriedade é declarada e automaticamente nomeada para corresponder aos seus tipos. Uma linha de código também é adicionada para inicializar o campo ou a propriedade no corpo do construtor.

   ![Resultado da geração do construtor](media/constructor5-result-cs.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)