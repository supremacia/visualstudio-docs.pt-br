---
title: "Misto código e informações ausentes na janela pilha de chamadas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a234529f13217cabf59a8d3827427e2f5341fb53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Código misto e informações ausentes na janela Pilha de Chamadas
Devido às diferenças entre as pilhas de chamadas para código gerenciado e nativo, o depurador nem sempre pode mostrar a pilha de chamadas completa quando os tipos de código são misturados. Quando código nativo chama código gerenciado, você pode observar as discrepâncias a seguir no **pilha de chamadas** janela:  
  
-   O quadro nativo imediatamente acima do código gerenciado pode estar ausente do **pilha de chamadas** janela. Para obter mais informações, consulte [como: sair do código gerenciado quando quadros nativos não forem encontrados na janela de pilha de chamadas](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Para aplicativos de modo misto iniciados fora do depurador, o **pilha de chamadas** janela pode exibir somente o código gerenciado e nenhum dos frames nativos estará visível.  
  
 Ambos os casos são razoavelmente incomuns. Na maioria das chamadas nativas para o código gerenciado, as pilhas de chamadas são exibidas corretamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md)