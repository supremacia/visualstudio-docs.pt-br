---
title: ADDRESS_KIND | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
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
ms.openlocfilehash: 331c5f0e3356a20ea61ac88108c1580bf4928737
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="addresskind"></a>ADDRESS_KIND
Specifies the kinds of addresses.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Terms  
 ADDRESS_KIND_NATIVE  
 A native address, represented by the [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) structure.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 An unmanaged address relative to a `this` (`Me` in Visual Basic) pointer and represented by the [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) structure.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 An unmanaged physical address, represented by the [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) structure.  
  
 ADDRESS_KIND_METHOD  
 A method of a class, represented by the [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) structure.  
  
 ADDRESS_KIND_FIELD  
 A field of a class, represented by the [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) structure.  
  
 ADDRESS_KIND_LOCAL  
 The address is for a local variable and is represented by the [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) structure.  
  
 ADDRESS_KIND_PARAM  
 A method or function parameter, represented by the [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) structure.  
  
 ADDRESS_KIND_ARRAYELEM  
 An array element, represented by the [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) structure.  
  
 ADDRESS_KIND_RETVAL  
 A return value, represented by the [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) structure.  
  
## <a name="remarks"></a>Remarks  
 The [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) method returns the [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure which contains a union of possible structures, the [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure. The `dwKind` field of the `DEBUG_ADDRESS_UNION` structure holds the `ADDRESS_KIND` value and describes how to interpret the union field.  
  
## <a name="requirements"></a>Requirements  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)