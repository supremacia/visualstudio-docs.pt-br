---
title: "Opções de revisão (herdado) de depuração | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: beb4191b56bb0b2b0d80b30aa7956bc23d0cfa9d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="debug-stepping-options-legacy"></a>Opções de avançar de depuração (legados)
Este tópico descreve como depurar [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos que têm atividades simultâneas no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Quando você está depurando atividades herdadas com execução simultânea, tais como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções a seguir para depurar seu código .

-   **Avançar de ramificação.** Este modo de depuração permite que você percorrer e depurar uma ramificação específica de uma atividade composta, como o **ParallelActivity** ou **ConditionalActivityGroup** atividade. Quando você usa esta opção depuração, você não irá notar que uma alteração no controle ocorre devido à execução simultânea de outras atividades no fluxo de trabalho. As etapas do depurador somente com as atividades na ramificação atualmente selecionado quando outras atividades no fluxo de trabalho podem executar simultaneamente. Por exemplo, por padrão, a ramificação mais à esquerda em um **ParallelActivity** atividade e a primeira atividade filho de um **ConditionedActivityGroup** atividade são usados para depuração. Se o usuário estiver interessado em depurar qualquer outra atividade de ramificação ou filhos, um ponto de interrupção explícito deve ser colocado na atividade de ramificação ou filho. Depuração continua naquela ramificação quando o ponto de interrupção é disparado.

-   **Avançar de instância.** Este modo de avançar permite que você entrar completamente e depurar executar simultaneamente atividades no fluxo de trabalho. Com essa opção, você observará que uma alteração no controle ocorre ao executar simultaneamente atividades é executado dentro de fluxo de trabalho.

 Por padrão, a opção de avançar da ramificação é selecionada, e os usuários podem alternar entre as duas opções para depurar um fluxo de trabalho herdado.

 Você deve selecionar a opção de avançar da instância ao depurar fluxos de trabalho herdados do computador de estado.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)
- [Como alterar a opção de executar a depuração em etapas (herdado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)