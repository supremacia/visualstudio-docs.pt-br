---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugParsedExpression::EvaluateSync
helpviewer_keywords: IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 261359ae3dc82f8544d0f48cf0e8f1103ccedd5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Esse método avalia a expressão analisada e, opcionalmente, converte o resultado em outro tipo de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwEvalFlags`  
 [in] Uma combinação de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) constantes que controlam como a expressão será avaliada.  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, de espera antes de retornar desse método. Use `INFINITE` aguardar indefinidamente.  
  
 `pSymbolProvider`  
 [in] O provedor de símbolo, expressado como um [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface.  
  
 `pAddress`  
 [in] O local atual de execução dentro de um método, expressado como um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pBinder`  
 [in] O associador, expressado como um [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface.  
  
 `bstrResultType`  
 [in] O tipo de resultado deve ser convertido em. Esse argumento pode ser um valor nulo.  
  
 `ppResult`  
 [out] Retorna o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface que representa os resultados da avaliação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O contexto de avaliação de expressão é determinado pelo `pAddress`, que torna possível determinar o método que a contém e, em seguida, regras de escopo do idioma usado para determinar o valor dos símbolos na expressão.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)