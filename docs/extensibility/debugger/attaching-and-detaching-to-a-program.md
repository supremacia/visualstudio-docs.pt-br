---
title: Anexar e desanexar para um programa | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5b0783cd011c91b9592479c7b64c6cb6a1afaa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-and-detaching-to-a-program"></a>Anexar e desanexar para um programa
Anexar o depurador requer o envio de sequência correta de métodos e eventos com os atributos apropriados.  
  
## <a name="sequence-of-methods-and-events"></a>Sequência de métodos e eventos  
  
1.  O Gerenciador de sessão de depuração (SDM) chama o [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
     Com base no modelo de processo do mecanismo (DE) de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração foi anexado com êxito para o programa. Caso contrário, o [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado para concluir o processo de conexão.  
  
     Se `S_OK` for retornado, é o DE ser carregado no mesmo processo que o SDM. O SDM executa as seguintes tarefas:  
  
    1.  Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.  
  
    2.  Cria conjunta DE.  
  
    3.  Chamadas [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  O envia DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
3.  O envia DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
4.  O envia DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para SDM com um `EVENT_SYNC_STOP` atributo.  
  
 Desanexação de um programa é um simples, o processo de duas etapas, da seguinte maneira:  
  
1.  As chamadas SDM [desanexar](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  O envia DE um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)