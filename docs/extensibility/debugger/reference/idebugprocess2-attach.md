---
title: IDebugProcess2::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
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
ms.openlocfilehash: 95b86696abe1491c4ff1deedcfa948d0ca6e0df4
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Attaches the session debug manager (SDM) to the process.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pCallback`  
 [in] An [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) object that is used for debug event notification.  
  
 `rgguidSpecificEngines`  
 [in] An array of GUIDs of debug engines to be used to debug programs running in the process. This parameter can be a null value. See Remarks for details.  
  
 `celtSpecificEngines`  
 [in] The number of debug engines in the `rgguidSpecificEngines` array and the size of the `rghrEngineAttach` array.  
  
 `rghrEngineAttach`  
 [in, out] An array of HRESULT codes returned by the debug engines. The size of this array is specified in the `celtSpecificEngines` parameter. Each code is typically either `S_OK` or `S_ATTACH_DEFERRED`. The latter indicates that the DE is currently attached to no programs.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code. The following table shows other possible values.  
  
|Value|Description|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|The specified process is already attached to the debugger.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|A security violation occurred during the attach procedure.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|A desktop process cannot be attached to the debugger.|  
  
## <a name="remarks"></a>Remarks  
 Attaching to a process attaches the SDM to all programs running in that process that can be debugged by the debug engines (DE) specified in the `rgguidSpecificEngines` array. Set the `rgguidSpecificEngines` parameter to a null value or include `GUID_NULL` in the array to attach to all programs in the process.  
  
 All debug events that occur in the process are sent to the given [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) object. This `IDebugEventCallback2` object is provided when the SDM calls this method.  
  
## <a name="see-also"></a>See Also  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)