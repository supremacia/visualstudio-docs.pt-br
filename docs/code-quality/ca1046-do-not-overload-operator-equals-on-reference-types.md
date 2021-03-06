---
title: "CA1046: Não sobrecarregar o operador equals em tipos de referência | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 87c9b1ca85eb7edaf1050da96356640b06b66e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: não sobrecarregar igualdades de operador em tipos de referência
|||  
|-|-|  
|NomeDoTipo|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo de referência pública pública ou aninhada sobrecarrega o operador de igualdade.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova a implementação do operador de igualdade.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando o tipo de referência se comporta como um tipo de valor interno. Se ele é significativo para fazer a adição ou subtração em instâncias do tipo, está provavelmente correto implementar o operador de igualdade e suprimir a violação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o comportamento padrão ao comparar duas referências.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O aplicativo a seguir compara algumas referências.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **um = novo (2,2) e b = novo (2,2) são iguais? Não**  
**c e a são igual? Sim**  
**b e a são = =? Não**  
**c e a são = =? Sim**   
## <a name="related-rules"></a>Regras relacionadas  
 [CA1013: sobrecarregar operador Equals ao sobrecarregar adicionar e subtrair](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators)