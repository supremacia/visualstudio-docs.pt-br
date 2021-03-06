---
title: "CA1402: Evitar sobrecargas em interfaces visíveis COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9294e1aab07aa05bc10de507e0a5885a47ebcc40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: evitar sobrecargas em interfaces visíveis COM
|||  
|-|-|  
|NomeDoTipo|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um modelo COM (Component Object) interface visível declarar métodos sobrecarregados.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando os métodos sobrecarregados são expostos a clientes COM, apenas a primeira sobrecarga do método mantém seu nome. Sobrecargas subsequentes são renomeadas exclusivamente por meio do acréscimo para o nome de um caractere de sublinhado '_' e um número inteiro que corresponde à ordem de declaração da sobrecarga. Por exemplo, considere os seguintes métodos.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Esses métodos são expostos aos clientes COM o seguinte.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Clientes COM do Visual Basic 6 não podem implementar métodos de interface usando um sublinhado no nome.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, renomeie os métodos sobrecarregados para que os nomes sejam exclusivos. Como alternativa, fazer a interface invisível COM alterando a acessibilidade ao `internal` (`Friend` na [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo definido como `false`.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma interface que viola a regra e uma interface que satisfaz a regra.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: evitar membros estáticos em tipos visíveis em COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)   
 [Tipo de Dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)