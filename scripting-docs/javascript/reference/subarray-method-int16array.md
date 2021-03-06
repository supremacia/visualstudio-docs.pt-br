---
title: "Método (Int16Array) subarray | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a7437c2-8c4e-41eb-a3d5-ec4f7399b81d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5407787f07c36c88da224b1addcda02c486e7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int16array"></a>Método subarray (Int16Array)
Obtém uma nova exibição Int16Array do [ArrayBuffer Object](../../javascript/reference/arraybuffer-object.md) armazenar para essa matriz, especificando o primeiro e o último membro da submatriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
var newInt16Array = int16Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newInt16Array`  
 A submatriz retornada por este método.  
  
 `begin`  
 O índice do início da matriz.  
  
 `end`  
 O índice do final da matriz. Ele não é inclusivo.  
  
## <a name="remarks"></a>Comentários  
 Se `begin` ou `end` for negativo, a referência será a um índice do final da matriz, e não do início. Se `end` não for especificado, a submatriz conterá todos os elementos desde o begin até o final da matriz tipada. O intervalo especificado pelos valores de `begin` e `end` é fixado ao intervalo válido do índice para a matriz atual. Se o tamanho calculado da nova matriz digitada for negativo, ele será fixado como zero. A matriz retornada é do mesmo tipo da matriz na qual esse método é invocado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter uma submatriz de dois elementos, começando com o primeiro elemento dessa matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Int16Array(buffer.byteLength / 2);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]