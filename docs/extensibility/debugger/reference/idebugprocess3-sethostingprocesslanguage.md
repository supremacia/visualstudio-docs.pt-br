---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
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
ms.openlocfilehash: 094163bb1fd5b44e82d966a3090d3caedfbf626e
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
This method sets the language that the process will be hosted under. This language can then be used by the debug engine (DE) to load the appropriate expression evaluator.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```csharp  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `guidLang`  
 [in] `GUID` of the language that the DE should use. Specify `GUID_NULL` (C++) or `Guid.Empty` (C#) to have the DE use the default language.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns error code.  
  
## <a name="remarks"></a>Remarks  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) can be used to retrieve the current language setting.  
  
## <a name="see-also"></a>See Also  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)