---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 0c5c751e392e8b34a7de598558b27360beab3352
ms.contentlocale: pt-br
ms.lasthandoff: 08/24/2017

---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Specifies the criteria for comparing two document contexts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```cs  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Members  
 DOCCONTEXT_EQUAL  
 Find the first document context in the list that is equal to the target document context.  
  
 DOCCONTEXT_LESS_THAN  
 Find the first document context in the list that is less than the target document context.  
  
 DOCCONTEXT_GREATER_THAN  
 Find the first document context in the list that is greater than the target document context.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Find the first document context in the list that is in the same document as the target document context.  
  
## <a name="remarks"></a>Remarks  
 Passed as an argument to the [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) method.  
  
 These values are used to specify a comparison criteria for finding the first document context in a list. A document context is given a list of document contexts to compare itself against through the `IDebugDocumentContext2::Compare` method. The first document context in the list for which the comparison operator is `true` is then returned.  
  
## <a name="requirements"></a>Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Enumerations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)