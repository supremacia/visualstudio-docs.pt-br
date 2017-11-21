---
title: "Alterar assinatura do método - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 64b37bca-92b8-4154-9d65-54073e5740fc
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.openlocfilehash: 83d1329706f53b1e5474a0a2cc4c859f0e982096
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="change-a-method-signature-in-visual-basic"></a>Alterar uma assinatura de método no Visual Basic
**O que:** permite que você remover ou alterar a ordem dos parâmetros do método.

**Quando:** você deseja mover ou remover um parâmetro de método que está sendo usado em uma variedade de locais.  

**Motivo:** você pode manualmente remover e reordenar os parâmetros e, em seguida, localizar todas as chamadas para esse método e alterá-los um por um, mas que poderiam levar a erros.  Essa ferramenta refatoração executará a tarefa automaticamente.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do nome do método para modificar, ou um de seus usos:

   ![Código realçado](media/changesignature_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + V**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **alterar assinatura** do popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Remover parâmetros**.
     * Selecione **Editar > Refatorar > reordenar parâmetros**.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **alterar assinatura** do popup da janela de visualização.

1. No **alterar assinatura** caixa de diálogo que aparecer, você pode usar os botões à direita para alterar a assinatura do método:

   ![Caixa de diálogo Alterar assinatura](media/changesignature_dialog.png)

   | Botão | Descrição
   | ------ | ---
   | **Para cima/baixo** | Mova o parâmetro selecionado para cima e lista
   | **Removerr**  | Remova o parâmetro selecionado da lista
   | **Restaurar** | Restaurar o parâmetro selecionado, riscado à lista

   > [!TIP]
   > Use o [ **visualizar alterações de referência** ](../../ide/preview-changes.md) caixa de seleção para ver qual será o resultado antes de confirmá-la.

1. Quando tiver terminado, pressione a **Okey** botão para fazer as alterações.

   ![Alterar o resultado de assinatura](media/changesignature_result.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (Visual Basic)](../refactoring-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)