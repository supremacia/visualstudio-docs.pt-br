---
title: EXCEPTION_STATE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
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
ms.openlocfilehash: 7cf3f0726e250fd0f7b1b9af768ffac85cbb8ec3
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Specifies the exception state.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Members  
 EXCEPTION_NONE  
 Do not stop at the exception.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Stop at first firing of exception. When describing an exception event, this flag indicates that the exception event is a first-chance exception event.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Stop at second firing of exception. When describing an exception event, indicates that the exception event is a second-chance exception event.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Stop at first firing of a user mode exception. When describing an exception event, indicates that the exception event is a first-chance user exception event.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Stop when a user mode exception is not caught. When describing an exception event, indicates that the exception event is an uncaught user mode exception event.  
  
 EXCEPTION_STOP_ALL  
 Stop on any exception. Not used when describing an exception event.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 When describing an exception event, indicates that the exception cannot be continued from.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indicates that the exception has code supporting it. Used in displaying an exception  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indicates that the exception code should be displayed in hexadecimal. Used in displaying an exception.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indicates that the exception code supports JustMyCode. Used in displaying an exception.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indicates that the managed code debugger should handle exceptions. If not set, the default debugger handles the exceptions. This is passed to the [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) method and not used in the [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 OBSOLETE, DO NOT USE.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 OBSOLETE, DO NOT USE.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 OBSOLETE, DO NOT USE.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 OBSOLETE, DO NOT USE.  
  
## <a name="remarks"></a>Remarks  
 Used as the `dwState` member of the [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) structure to indicate the state of the exception and what can be done about it.  
  
 These values are also passed to the [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) method to set the state of all exceptions.  
  
 These flags may be combined with a bitwise OR.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)