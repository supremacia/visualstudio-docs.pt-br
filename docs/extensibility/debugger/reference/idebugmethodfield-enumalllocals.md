---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
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
ms.openlocfilehash: 509586c2fc70e39195275becd417cffd1605df3e
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Creates an enumerator for all local variables of the method, including those generated internally by a compiler.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pAddress`  
 [in] An [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) object representing a debug address within the method, pointing to a particular scope or context.  
  
 `ppLocals`  
 [out] Returns an [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) object representing the list of all locals in the specified scope; otherwise, returns a null value indicating no locals.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns S_OK or returns S_FALSE if there are no locals. Otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 Only the variables defined within the block that contains the given debug address are enumerated. This method includes any compiler-generated locals. If all that is needed are the locals explicitly defined in the source, call the [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) method.  
  
 A method can contain multiple scoping contexts or blocks.  
  
## <a name="see-also"></a>See Also  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)