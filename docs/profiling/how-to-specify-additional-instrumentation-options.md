---
title: "Como especificar opções de instrumentação adicionais | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8052c0538619588f60fd21802209d57bd7fdf80d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Como especificar opções de instrumentação adicionais

Você pode instrumentar binários usando o IDE do Visual Studio ou usando ferramentas de linha de comando. Se você instrumentar um binário do IDE, será possível controlar o volume de dados coletados durante a instrumentação, especificando opções de instrumentação adicionais para a ferramenta [VSInstr](../profiling/vsinstr.md). Essas opções estão disponíveis no nível de sessão ou de destino. Por exemplo, para incluir ou excluir funções específicas durante o processo de instrumentação, use a opção adicional de instrumentação no nível de destino.

> [!IMPORTANT]
> Cada investigação que é inserida modifica ligeiramente o comportamento do programa original. Essa modificação gera sobrecarga no tempo de análise. Mesmo que uma aproximação dessa sobrecarga seja subtraída, ela ainda tem efeitos de temporização sutis em aplicativos com multithread. As opções de ferramenta [VSInstr](../profiling/vsinstr.md) ajudam a controlar a coleta de dados durante a criação de perfil.

## <a name="to-specify-additional-instrumentation-option"></a>Como especificar opções de instrumentação adicionais

1. No **Gerenciador de Desempenho**, selecione a **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.

2. Nas **Páginas de Propriedades**, clique nas propriedades **Avançadas**.

3. Digite opções na caixa **Opções de instrumentação adicionais**.

     Por exemplo, use /CONTROL:THREAD para especificar o nível de criação de perfil. Para obter uma lista completa das opções, consulte [VSInstr](../profiling/vsinstr.md).

4. Clique em **OK**.

## <a name="see-also"></a>Consulte também

[Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)  
[Criando perfil na linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)