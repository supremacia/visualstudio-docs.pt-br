---
title: IDiaStackWalker | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 68cf4cf206d243762247b36161f349cc2a1387cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fornece métodos para fazer uma pilha percorrer usando as informações no arquivo. PDB.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDiaStackWalker: IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDiaStackWalker`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera um enumerador de quadro de pilha para x86 de plataformas.|  
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera um enumerador de quadro de pilha para um tipo de plataforma específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é usada para obter uma lista de quadros de pilha para um módulo carregado. Cada um dos métodos é passada um [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objeto (implementado pelo aplicativo cliente) que fornece as informações necessárias para criar a lista de quadros de pilha.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é obtida chamando o `CoCreateInstance` método com o identificador de classe `CLSID_DiaStackWalker` e a ID de interface de `IID_IDiaStackWalker`. O exemplo mostra como essa interface é obtida.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como obter o `IDiaStackWalker` interface.  
  
```C++  
  
      IDiaStackWalker* pStackWalker;  
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaStackWalker,  
                              (void**) &pStackWalker);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces (SDK de acesso à Interface de depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)