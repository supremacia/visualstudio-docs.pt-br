---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_INFO_FIELDS
helpviewer_keywords: MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d96175501d0e75ee1949847c69909c23a3b08582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Especifica os sinalizadores de módulo para informações de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Membros  
 MIF_NONE  
 Inicializar/usar nenhum dos campos na estrutura.  
  
 MIF_NAME  
 Inicializar/usar o `m_bstrName` campo o [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura.  
  
 MIF_URL  
 Inicializar/usar o `m_bstrUrl` campo o `MODULE_INFO` estrutura.  
  
 MIF_VERSION  
 Inicializar/usar o `m_bstrVersion` campo o `MODULE_INFO` estrutura.  
  
 MIF_DEBUGMESSAGE  
 Inicializar/usar o `m_bstrDebugMessage` campo o `MODULE_INFO` estrutura.  
  
 MIF_LOADADDRESS  
 Inicializar/usar o `m_addrLoadAddress` campo o `MODULE_INFO` estrutura.  
  
 MIF_PREFFEREDADDRESS  
 Inicializar/usar o `m_addrPreferredLoadAddress` campo o `MODULE_INFO` estrutura.  
  
 MIF_SIZE  
 Inicializar/usar o `m_dwSize` campo o `MODULE_INFO` estrutura.  
  
 MIF_LOADORDER  
 Inicializar/usar o `m_dwLoadOrder` campo o `MODULE_INFO` estrutura.  
  
 MIF_TIMESTAMP  
 Inicializar/usar o `m_TimeStamp` campo o `MODULE_INFO` estrutura.  
  
 MIF_URLSYMBOLLOCATION  
 Inicializar/usar o `m_bstrUrlSymbolLocation` campo o `MODULE_INFO` estrutura.  
  
 MIF_FLAGS  
 Inicializar/usar o `m_dwModuleFlags` campo o `MODULE_INFO` estrutura.  
  
 MIF_ALLFIELDS  
 Inicializar/usar todos os campos no `MODULE_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados como um argumento para o [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) método para indicar quais campos do [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura devem ser inicializado.  
  
 Esses valores também são usados no `MODULE_INFO` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)