---
title: "CA1005: Evitar parâmetros excessivos em tipos genéricos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3bbf8dae17c9f0fd257388d8520485bf1a5d6970
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: evitar parâmetros excessivos em tipos genéricos
|||  
|-|-|  
|NomeDoTipo|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo genérico visível externamente tem mais de dois parâmetros de tipo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quanto mais parâmetros de tipo um tipo genérico contiver, mais difícil será saber e lembrar-se do que cada parâmetro de tipo representa. É geralmente óbvio com um parâmetro de tipo, como em `List<T>`e, em certos casos com dois parâmetros de tipo, como em `Dictionary<TKey, TValue>`. Se houver mais de dois parâmetros de tipo, a dificuldade torna-se muito grande para a maioria dos usuários (por exemplo, `TooManyTypeParameters<T, K, V>` em c# ou `TooManyTypeParameters(Of T, K, V)` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o design para usar não mais do que dois parâmetros de tipo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso dessa regra, a menos que o design absolutamente requer mais de dois parâmetros de tipo. Fornecer genéricos em uma sintaxe que seja fácil de entender e usar reduz o tempo que é necessário para saber mais e aumenta a taxa de adoção de novas bibliotecas.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Consulte também  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)