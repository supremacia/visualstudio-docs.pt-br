---
title: "CA1049: Tipos que possuem recursos nativos devem ser descartáveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d387cd29b0c17bdb31db495fe42146cf1a886d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: tipos que tenham recursos nativos devem ser descartáveis
|||  
|-|-|  
|NomeDoTipo|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Faz referência a um tipo de um <xref:System.IntPtr?displayProperty=fullName> campo, uma <xref:System.UIntPtr?displayProperty=fullName> campo, ou um <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> campo, mas não implementa <xref:System.IDisposable?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra supõe que <xref:System.IntPtr>, <xref:System.UIntPtr>, e <xref:System.Runtime.InteropServices.HandleRef> campos armazenam ponteiros para os recursos não gerenciados. Os tipos que alocam recursos não gerenciados devem implementar <xref:System.IDisposable> para permitir que os chamadores para liberar os recursos sob demanda e reduzir os tempos de vida dos objetos que contêm os recursos.  
  
 O padrão de design recomendado para limpar os recursos não gerenciados é fornecer um implícito e meios explícito para liberar os recursos usando o <xref:System.Object.Finalize%2A?displayProperty=fullName> método e o <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método, respectivamente. O coletor de lixo chama o <xref:System.Object.Finalize%2A> método de um objeto em algum momento indeterminado depois que o objeto é determinado pode não ser alcançado. Depois de <xref:System.Object.Finalize%2A> é chamado, adicional coleta de lixo é necessário para liberar o objeto. O <xref:System.IDisposable.Dispose%2A> método permite que o chamador explicitamente liberar recursos sob demanda, antes do que os recursos deve ser liberados se da esquerda para o coletor de lixo. Depois que ele limpa os recursos não gerenciados, <xref:System.IDisposable.Dispose%2A> devem chamar o <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> método para permitir que o coletor de lixo Saiba que <xref:System.Object.Finalize%2A> não precisa ser chamado; isso elimina a necessidade para a coleta de lixo adicionais e reduz o tempo de vida do objeto.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, implementar <xref:System.IDisposable>.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o tipo não faz referência a um recurso não gerenciado. Caso contrário, não suprimir um aviso dessa regra porque não implementar <xref:System.IDisposable> pode fazer com que os recursos não gerenciados para se tornar indisponível ou subutilizados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que implementa <xref:System.IDisposable> para limpar um recurso não gerenciado.  
  
 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2115: chamar GC.KeepAlive durante o uso de recursos nativos](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: tipos que têm campos descartáveis devem ser descartáveis](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## <a name="see-also"></a>Consulte também  
 [Limpando recursos não gerenciados](/dotnet/standard/garbage-collection/unmanaged)   
 [Padrão de descarte](/dotnet/standard/design-guidelines/dispose-pattern)