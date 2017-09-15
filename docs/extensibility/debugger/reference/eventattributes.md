---
title: EVENTATTRIBUTES | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 10
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: fff378260ab2136e6f8917d10d4669911dac3faa
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Specifies the event attributes.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Members  
 EVENT_ASYNCHRONOUS  
 Indicates that the event is asynchronous and no reply to the event is needed.  
  
 EVENT_SYNCHRONOUS  
 Indicates that the event is synchronous; reply by means of [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Indicates that this is a stopping event. Must be combined with either `EVENT_ASYNCHRONOUS` or `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Indicates an asynchronous stopping event. There is currently no such event. This flag is only a placeholder.  
  
 EVENT_SYNC_STOP  
 Indicates a synchronous stopping event (a combination of `EVENT_SYNCHRONOUS` and `EVENT_STOPPING`). This value is used by a debug engine (DE) when it sends a stopping event. The reply is made by means of a call to [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md), or [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Indicates an event that is sent immediately and synchronously to the IDE. This flag is combined with other flags like `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, or `EVENT_SYNC_STOP` to indicate the type of event and the fact that the reply mechanism (if any) is known.  
  
 EVENT_EXPRESSION_EVALUATION  
 The event is a result of expression evaluation.  
  
## <a name="remarks"></a>Remarks  
 These values are passed in the `dwAttrib` parameter of the [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) method.  
  
 These values may be combined with a bitwise `OR`.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)