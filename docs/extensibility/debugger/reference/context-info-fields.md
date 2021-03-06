---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8f0316e8822706b26103f02eda1849568cf79994
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Especifica quais informações recuperar sobre um contexto de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Membros  
 CIF_MODULEURL  
 Inicializar/usar o `bstrModuleUrl` campo o [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estrutura.  
  
 CIF_FUNCTION  
 Inicializar/usar o `bstrFunction` campo o `CONTEXT_INFO` estrutura.  
  
 CIF_FUNCTIONOFFSET  
 Inicializar/usar o `posFunctionOffset` campo o `CONTEXT_INFO` estrutura.  
  
 CIF_ADDRESS  
 Inicializar/usar o `bstrAddress` campo o `CONTEXT_INFO` estrutura.  
  
 CIF_ADDRESSOFFSET  
 Inicializar/usar o `bstrAddressOffset` campo o `CONTEXT_INFO` estrutura.  
  
 CIF_ALLFIELDS  
 Todos os campos de inicialização/usar o `CONTEXT_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados de um parâmetro para o [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método para indicar quais campos do [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estrutura devem ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `CONTEXT_INFO` estrutura são válidos e usadas quando a estrutura é retornada.  
  
 Esses valores podem ser combinados com um OR bit a bit.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)