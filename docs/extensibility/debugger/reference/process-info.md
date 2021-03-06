---
title: PROCESS_INFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROCESS_INFO
helpviewer_keywords: PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5628e3cca48799b602917fa1504479b46ee02dd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="processinfo"></a>PROCESS_INFO
Contém informações sobre um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Membros  
 Campos  
 Uma combinação de sinalizadores do [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumeração que especificam quais campos são preenchidos.  
  
 bstrFileName  
 O nome de caminho completo do processo. Equivalente a chamar o [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) método com o parâmetro `GN_FILENAME`.  
  
 bstrBaseName  
 O nome de arquivo e extensão do processo. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_BASENAME`.  
  
 bstrTitle  
 O título do processo, se houver. Equivalente a chamar o `IDebugProcess2::Getname` método com o parâmetro `GN_TITLE`.  
  
 ProcessId  
 O [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que identifica o processo. Equivalente a chamar o [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) método.  
  
 dwSessionId  
 O identificador da sessão de depuração que esse processo está em execução no.  
  
 bstrAttachedSessionName  
 O nome da sessão anexado. Equivalente a chamar o [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) método.  
  
 CreationTime  
 A hora em que o processo foi criado.  
  
 Sinalizadores  
 Uma combinação de sinalizadores do [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) enumeração que especificam propriedades do processo.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método em que ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)