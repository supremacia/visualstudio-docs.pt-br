---
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
caps.latest.revision: 9
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
ms.openlocfilehash: 889f350fed8dfaf3c052b3f9fc22f4480ea23737
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="bpresolutioncode"></a>BP_RESOLUTION_CODE
Descreve o local de um ponto de interrupção do código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _BP_RESOLUTION_CODE {   
   IDebugCodeContext2* pCodeContext;  
} BP_RESOLUTION_CODE;  
```  
  
```csharp  
public struct BP_RESOLUTION_CODE {   
   public IDebugCodeContext2 pCodeContext;  
};  
```  
  
## <a name="members"></a>Membros  
 `pCodeContext`  
 O [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que identifica a posição do ponto de interrupção no código.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é um membro do [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) estrutura, que está em um membro de ativar o [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estrutura retornada pelo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)