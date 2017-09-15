---
title: Modos operacionais | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 34a806f5513632fcd17533e9c43abe22980a542d
ms.lasthandoff: 02/22/2017

---
# <a name="operational-modes"></a>Modos operacionais
Existem três modos em que o IDE pode operar, da seguinte maneira:  
  
-   [Modo de design](#vsconoperationalmodesanchor1)  
  
-   [Modo de execução](#vsconoperationalmodesanchor2)  
  
-   [Modo de interrupção](#vsconoperationalmodesanchor3)  
  
 Como o mecanismo de depuração personalizado (DE) faz a transição entre os modos é uma decisão de implementação que exige que você esteja familiarizado com os mecanismos de transição. O DE pode ou não pode implementar diretamente esses modos. Esses modos são realmente pacote modos de depuração que mudar com base na ação do usuário ou DE eventos. Por exemplo, a transição do modo de execução em modo de interrupção é atraiu por um evento de interrupção a partir DE. A transição de interrupção para executar modo ou etapa é atraiu pelo usuário que está executando operações como etapa ou Execute. Para obter mais informações sobre DE transições, consulte [controle de execução](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="a-namevsconoperationalmodesanchor1a-design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Modo de design  
 Modo de design é o estado nonrunning de depuração do Visual Studio, durante esse período, você pode definir recursos em seu aplicativo de depuração.  
  
 Depuração somente alguns recursos são usados durante o modo design. Um desenvolvedor pode optar por definir pontos de interrupção ou criar expressões de inspeção. O DE nunca é carregado ou chamado enquanto o IDE está no modo de design. Interação com o DE ocorre durante apenas modos de execução e quebra.  
  
##  <a name="a-namevsconoperationalmodesanchor2a-run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Modo de execução  
 Modo de execução ocorre quando um programa é executado em uma sessão de depuração no IDE. O aplicativo é executado até o encerramento, até um ponto de interrupção é atingido, ou até que uma exceção é lançada. Quando o aplicativo é executado até o encerramento, as transições DE no modo de design. Quando um ponto de interrupção é atingido ou uma exceção é lançada, o DE transição para o modo de interrupção.  
  
##  <a name="a-namevsconoperationalmodesanchor3a-break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Modo de interrupção  
 Modo de interrupção ocorre quando a execução do programa de depuração é suspensa. Modo de interrupção oferece ao desenvolvedor um instantâneo do aplicativo no momento da quebra e permite que o desenvolvedor analisar o estado do aplicativo e alterar como o aplicativo será executado. O desenvolvedor pode exibir e editar o código, examinar ou modificar dados, reinicie o aplicativo, encerrar a execução ou continuar a execução do mesmo.  
  
 Modo de interrupção é inserido quando o DE envia um evento de parada síncrona. Eventos de interrupção síncrona, também chamados de eventos de interrupção, notificam o Gerenciador de sessão de depuração (SDM) e o IDE que o aplicativo que está sendo depurado parou a execução de código. O [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfaces são exemplos de eventos de interrupção.  
  
 Interrompendo eventos continuam por uma chamada para um dos métodos a seguir, que o depurador de modo de interrupção para executar ou depurar o modo de transição:  
  
-   [Executar](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Etapa](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="a-namevsconoperationalmodesanchor4a-step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Modo de etapa  
 Modo de etapa ocorre quando o programa de etapas para a próxima linha de código, ou em, acima ou fora de uma função. Uma etapa é executada, chamando o método [etapa](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método requer `DWORD`que especificam o [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumerações como parâmetros de entrada.  
  
 Quando o programa com êxito as etapas para a próxima linha de código ou em uma função, ou ele é executado até o cursor ou para definir um ponto de interrupção, o DE automaticamente transições de volta para o modo de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)