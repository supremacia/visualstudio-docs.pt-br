---
title: ': Get_registerid | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Recupera o designador de registro do local quando o [enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) é definido como `LocIsEnregistered`.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna o designador de registro do local.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Se o símbolo é em relação a um registro, ou seja, se o símbolo [enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) é definido como `LocIsRegRel`, use o `get_registerId` método seguido por uma chamada para o [: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) método para obter o deslocamento do registro onde se encontra o símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)