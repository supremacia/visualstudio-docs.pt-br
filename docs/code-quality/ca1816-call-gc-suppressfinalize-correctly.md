---
title: 'CA1816: Call GC.SuppressFinalize correctly | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 43f0cf6749b6ad7a329f814aa9fbb19658912af9
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Call GC.SuppressFinalize correctly
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Category|Microsoft. Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
  
-   A method that is an implementation of <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> does not call <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   A method that is not an implementation of <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> calls <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   A method calls <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> and passes something other than this (Me in Visual Basic).  
  
## <a name="rule-description"></a>Rule Description  
 The <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> method lets users release resources at any time before the object becoming available for garbage collection. If the <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> method is called, it frees resources of the object. This makes finalization unnecessary. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> should call <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> so the garbage collector does not call the finalizer of the object.  
  
 To prevent derived types with finalizers from having to re-implement <xref:System.IDisposable> and to call it, unsealed types without finalizers should still call <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule:  
  
 If the method is an implementation of <xref:System.IDisposable.Dispose%2A>, add a call to <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 If the method is not an implementation of <xref:System.IDisposable.Dispose%2A>, either remove the call to <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> or move it to the type's <xref:System.IDisposable.Dispose%2A> implementation.  
  
 Change all calls to <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> to pass this (Me in Visual Basic).  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Only suppress a warning from this rule if you are deliberating using <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> to control the lifetime of other objects. Do not suppress a warning from this rule if an implementation of <xref:System.IDisposable.Dispose%2A> does not call <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. In this situation, failing to suppress finalization degrades performance and provide no benefits.  
  
## <a name="example"></a>Example  
 The following example shows a method that incorrectly calls <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)] [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>Example  
 The following example shows a method that correctly calls <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)] [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2215: Dispose methods should call base class dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: Disposable types should declare finalizer](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>See Also  
 [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)