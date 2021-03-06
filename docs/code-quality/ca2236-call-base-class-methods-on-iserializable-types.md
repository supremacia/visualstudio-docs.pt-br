---
title: "CA2236: Chamar métodos de classe base em tipos ISerializable | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c2e4db6ac698dba6a24bf0f485deb8b1d2e1488a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: chamar métodos de classe base em tipos ISerializable
|||  
|-|-|  
|NomeDoTipo|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo derivado de um tipo que implementa o <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface e uma das seguintes condições for verdadeira:  
  
-   O tipo implementa o construtor de serialização, ou seja, um construtor com a <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> a assinatura do parâmetro, mas não chama o construtor de serialização do tipo base.  
  
-   O tipo implementa o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método mas não chama o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método do tipo base.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Em um processo de serialização personalizada, um tipo implementa o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método para serializar seus campos e o construtor de serialização para desserializar os campos. Se o tipo é derivado de um tipo que implementa o <xref:System.Runtime.Serialization.ISerializable> interface, o tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> construtor de serialização e o método deve ser chamado para serializar/de-serialize os campos do tipo base. Caso contrário, o tipo de não ser serializado e desserializado corretamente. Observe que, se o tipo derivado não adicionar os novos campos, o tipo não necessário implementar o <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método nem o construtor de serialização ou chamar os equivalentes de tipo base.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame o tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> derivado de serialização ou método de construtor da correspondente construtor ou método de tipo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo derivado que satisfaz a regra chamando o construtor de serialização e <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método da classe base.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2240: implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../code-quality/ca2120-secure-serialization-constructors.md)