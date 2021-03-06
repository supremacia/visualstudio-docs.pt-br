---
title: "CA2134: Os métodos devem manter transparência consistente quando os métodos base | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 62438b49d91f680ae360f1d32f7cfe3b0efa2b75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: os métodos devem manter uma transparência consistente durante a substituição dos métodos base
|||  
|-|-|  
|NomeDoTipo|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Essa regra é acionado quando um método marcado com o <xref:System.Security.SecurityCriticalAttribute> substitui um método que é transparente ou marcados com o <xref:System.Security.SecuritySafeCriticalAttribute>. A regra também é acionado quando um método que é transparente ou marcados com o <xref:System.Security.SecuritySafeCriticalAttribute> substitui um método marcado com um <xref:System.Security.SecurityCriticalAttribute>.  
  
 A regra é aplicada durante a substituição de um método virtual ou a implementação de uma interface.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra é acionado em tentativas de alterar a acessibilidade de segurança de um método a cadeia de herança. Por exemplo, se um método virtual em uma classe base é crítico para segurança ou transparente, em seguida, a classe derivada deve substituí-la com um método crítico para segurança ou transparente. Por outro lado, se o virtual é crítico de segurança, a classe derivada deve substituí-la com um método de segurança crítica. A mesma regra aplica-se para implementar métodos de interface.  
  
 Regras de transparência são aplicadas quando o código é JIT compilado em vez de em tempo de execução, para que o cálculo de transparência não tem informações de tipo dinâmico. Portanto, o resultado do cálculo de transparência deve ser capaz de ser determinada exclusivamente dos tipos estáticos compilação JIT, independentemente do tipo dinâmico.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a transparência do método que está substituindo um método virtual ou implementando uma interface para corresponder a transparência de virtual ou o método de interface.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima avisos dessa regra. Violações desta regra resultará em um tempo de execução <xref:System.TypeLoadException> para assemblies que usam a transparência de nível 2.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Código transparente de segurança, nível 2](/dotnet/framework/misc/security-transparent-code-level-2)