---
title: 'CA1027: Mark enums with FlagsAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: b1b331010b2b0340c31b4a8a08c3b7ec6b6c7e04
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Mark enums with FlagsAttribute
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Category|Microsoft.Design|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 The values of a public enumeration are powers of two or are combinations of other values that are defined in the enumeration, and the <xref:System.FlagsAttribute?displayProperty=fullName> attribute is not present. To reduce false positives, this rule does not report a violation for enumerations that have contiguous values.  
  
## <a name="rule-description"></a>Rule Description  
 An enumeration is a value type that defines a set of related named constants. Apply <xref:System.FlagsAttribute> to an enumeration when its named constants can be meaningfully combined. For example, consider an enumeration of the days of the week in an application that keeps track of which day's resources are available. If the availability of each resource is encoded by using the enumeration that has <xref:System.FlagsAttribute> present, any combination of days can be represented. Without the attribute, only one day of the week can be represented.  
  
 For fields that store combinable enumerations, the individual enumeration values are treated as groups of bits in the field. Therefore, such fields are sometimes referred to as *bit fields*. To combine enumeration values for storage in a bit field, use the Boolean conditional operators. To test a bit field to determine whether a specific enumeration value is present, use the Boolean logical operators. For a bit field to store and retrieve combined enumeration values correctly, each value that is defined in the enumeration must be a power of two. Unless this is so, the Boolean logical operators will not be able to extract the individual enumeration values that are stored in the field.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, add <xref:System.FlagsAttribute> to the enumeration.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Suppress a warning from this rule if you do not want the enumeration values to be combinable.  
  
## <a name="example"></a>Example  
 In the following example, `DaysEnumNeedsFlags` is an enumeration that meets the requirements for using <xref:System.FlagsAttribute>, but does not have it. The `ColorEnumShouldNotHaveFlag` enumeration does not have values that are powers of two, but incorrectly specifies <xref:System.FlagsAttribute>. This violates rule [CA2217: Do not mark enums with FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2217: Do not mark enums with FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.FlagsAttribute?displayProperty=fullName>