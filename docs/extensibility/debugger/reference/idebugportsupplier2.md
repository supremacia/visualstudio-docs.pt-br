---
title: IDebugPortSupplier2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2
helpviewer_keywords: IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 257bbf334adbdfd3a93cf172de0b15bf63cb3217
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Essa interface fornece portas para o Gerenciador de sessão de depuração (SDM).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para representar um fornecedor de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para `CoCreateInstance` com um fornecedor de porta `GUID` retorna essa interface (Isso é uma forma comum de obter essa interface). Por exemplo:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Uma chamada para [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) retorna essa interface, que representa o fornecedor de porta atual que está sendo usado por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) retorna essa interface, que representa o fornecedor de porta que criou a porta.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa uma lista de `IDebugPortSupplier` interfaces (o `IEnumDebugPortSuppliers` interface é obtida do [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa todos os fornecedores de porta registrado com [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Um mecanismo de depuração normalmente não consegue interagir com um fornecedor de porta.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortSupplier2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtém o nome do fornecedor de porta.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtém o identificador de fornecedor de porta.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtém uma porta de um fornecedor de porta.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera as portas que já existem.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica se um fornecedor de porta dá suporte à adição de novas portas.|  
|[Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Adiciona uma porta.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Remove uma porta.|  
  
## <a name="remarks"></a>Comentários  
 Um fornecedor de porta pode identificar-se por nome e ID, adicionar e remover portas e enumerar todas as portas que fornece o fornecedor de porta.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)