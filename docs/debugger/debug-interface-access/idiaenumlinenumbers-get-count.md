---
title: Idiaenumlinenumbers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::get_Count method
ms.assetid: dbb55936-b754-4a27-8b82-9537a7adb664
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 979e2f6366deb9ed54f1ce3fedaa6b3ebbc18591
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumlinenumbersgetcount"></a>IDiaEnumLineNumbers::get_Count
Recupera o número de números de linha.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pRetVal  
 [out] Retorna o número de números de linha.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)