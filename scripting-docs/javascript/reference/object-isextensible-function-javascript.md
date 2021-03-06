---
title: "Função Object isextensible (JavaScript) | Microsoft Docs"
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
helpviewer_keywords:
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectisextensible-function-javascript"></a>Função Object.isExtensible (JavaScript)
Retorna um valor que indica se novas propriedades podem ser adicionadas a um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se o objeto é extensível, que indica que as novas propriedades podem ser adicionadas ao objeto; Caso contrário, `false`.  
  
## <a name="exceptions"></a>Exceções  
 Se o `object` argumento não é um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre como definir atributos de propriedade, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md). Para obter os atributos de uma propriedade, você pode usar o [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funções relacionadas  
 As seguintes funções relacionadas impedir a modificação de atributos de objeto.  
  
|Função|Objeto é feito não extensível|`configurable`é definido como `false` para cada propriedade|`writable`é definido como `false` para cada propriedade|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sim|Não|Não|  
|[Seal](../../javascript/reference/object-seal-function-javascript.md)|Sim|Sim|Não|  
|[Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sim|Sim|Sim|  
  
 Os seguintes funções retornam `true` se todas as condições marcadas na tabela a seguir forem verdadeiras.  
  
|Função|Objeto é extensível?|`configurable`é `false` para todas as propriedades?|`writable`é `false` para todas as propriedades de dados?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|`Object.isExtensible`|Sim|Não|Não|  
|[IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|Não|Sim|Não|  
|[IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Não|Sim|Sim|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Object.isExtensible`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Função Object seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Função Object Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Função Object IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Função Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)