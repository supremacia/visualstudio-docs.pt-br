---
title: "CA2104: Não declarar tipos de referência mutáveis somente leitura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bbd12d09c95f1ec93c7232901270cfbece311693
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: não declarar tipos de referência mutáveis somente leitura
|||  
|-|-|  
|NomeDoTipo|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente contém um campo somente leitura visível externamente que é um tipo de referência mutável.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um tipo mutável é um tipo cujos dados da instância podem ser modificados. O <xref:System.Text.StringBuilder?displayProperty=fullName> classe é um exemplo de um tipo de referência mutável. Ele contém membros que podem alterar o valor de uma instância da classe. Um exemplo de um tipo de referência imutável é o <xref:System.String?displayProperty=fullName> classe. Depois de instanciado, seu valor nunca pode mudar.  
  
 O modificador de somente leitura ([readonly](/dotnet/csharp/language-reference/keywords/readonly) em c#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) na [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e [const](/cpp/cpp/const-cpp) em C++) em um tipo de referência de campo (ponteiro em C++) impede que o campo substituído por uma instância diferente do tipo de referência. No entanto, o modificador não impede que os dados da instância do campo que está sendo modificado por meio do tipo de referência.  
  
 Campos de matriz de somente leitura são isentos dessa regra, mas em vez disso, causar uma violação do [CA2105: os campos de matriz não devem ser somente leitura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regra.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o modificador de somente leitura ou, se uma alteração significativa é aceitável, substitua o campo com um tipo imutável.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o tipo de campo é imutável.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma declaração de campo que faz com que uma violação desta regra.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]