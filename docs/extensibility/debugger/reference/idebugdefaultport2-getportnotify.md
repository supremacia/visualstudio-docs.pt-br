---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::GetPortNotify
helpviewer_keywords: IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 26eefb5dc1e30d9d9b8b6584159ce5f942b8e4e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Esse método obtém um [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface para essa porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppPortNotify`  
 [out] Um [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, o `QueryInterface` método é chamado no objeto que implementa o [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface para obter uma [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface. No entanto, há circunstâncias em que a interface desejada é implementada em um objeto diferente. Este método oculta nessas circunstâncias e retorna o `IDebugPortNotify2` interface do objeto mais apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)