---
title: 'CA2236: Call base class methods on ISerializable types | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
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
ms.openlocfilehash: ae87df4ff5efceee22fc76f6449ac8c3c9993e8b
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Call base class methods on ISerializable types
|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A type derives from a type that implements the <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, and one of the following conditions is true:  
  
-   The type implements the serialization constructor, that is, a constructor with the <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> parameter signature, but does not call the serialization constructor of the base type.  
  
-   The type implements the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> method but does not call the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method of the base type.  
  
## <a name="rule-description"></a>Rule Description  
 In a custom serialization process, a type implements the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method to serialize its fields and the serialization constructor to de-serialize the fields. If the type derives from a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface, the base type <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method and serialization constructor should be called to serialize/de-serialize the fields of the base type. Otherwise, the type will not be serialized and de-serialized correctly. Note that if the derived type does not add any new fields, the type does not need to implement the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method nor the serialization constructor or call the base type equivalents.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, call the base type <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method or serialization constructor from the corresponding derived type method or constructor.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows a derived type that satisfies the rule by calling the serialization constructor and <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method of the base class.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)] [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2240: Implement ISerializable correctly](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implement serialization methods correctly](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Mark all non-serializable fields](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Mark ISerializable types with SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Provide deserialization methods for optional fields](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Secure serialization constructors](../code-quality/ca2120-secure-serialization-constructors.md)