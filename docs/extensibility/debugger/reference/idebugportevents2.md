---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2
helpviewer_keywords: IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0a5782f0a50ac37b45c4b7e3402bcdded96b4683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Essa interface notifica um ouvinte (normalmente o depuração Gerenciador de sessão [SDM] ou um mecanismo de depuração) do programa e o processo de criação e destruição em uma porta específica. Essas informações podem ser usadas para apresentar uma exibição em tempo real dos processos e programas em execução na porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface para receber notificações sobre o programa de criação e destruição. Um mecanismo de depuração também pode implementar essa interface para monitorar esses eventos de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Todos os [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces podem ser consultadas para um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface. O <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> método `IDebugPortEvents2` é chamado <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface para obter um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface. Por fim, o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método no <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface é chamada para enviar os eventos por meio de [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) método.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra o método de `IDebugPortEvents2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envia eventos que descrevem a criação e destruição de processos e programas na porta.|  
  
## <a name="remarks"></a>Comentários  
 `IDebugPortEvents2`também é usado pelo SDM depurar programas que são executados em um processo que já está sendo depurado.  
  
 Eventos de porta são passados para o SDM por esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)