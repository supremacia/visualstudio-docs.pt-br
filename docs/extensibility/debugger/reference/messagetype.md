---
title: MESSAGETYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
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
ms.openlocfilehash: 2df884c0e6e6945ff22da6ff38dfef2cc0d63d29
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="messagetype"></a>MESSAGETYPE
Specifies the message type and reason.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Members  
 MT_OUTPUTSTRING  
 Indicates that the message should be sent to the output window. This is mutually exclusive from `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indicates that the message should be shown in a message box. This is mutually exclusive from `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 A mask value to isolate the destination for the message.  
  
 MT_REASON_EXCEPTION  
 Indicates that a message box is being shown as a result of an exception. This is mutually exclusive from `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indicates that a message box is being shown as a result of hitting a tracepoint. This is mutually exclusive to `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 A mask value to isolate the reason for the message being shown.  
  
## <a name="remarks"></a>Remarks  
 These values are returned from the [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) and [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) methods.  
  
 One of the reason values can be combined with one of the output destination values using a bitwise `OR`.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)