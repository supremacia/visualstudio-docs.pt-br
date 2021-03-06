---
title: 'CA1412: Marcar Interfaces ComSource como IDispatch | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b2523397f59affa2d7e1e60e69e7ba2047438135
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: marcar interfaces ComSource como IDispatch
|||  
|-|-|  
|NomeDoTipo|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo é marcado com o <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo e pelo menos uma interface especificada não está marcado com o <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo definido como o `InterfaceIsDispatch` valor.  
  
## <a name="rule-description"></a>Descrição da Regra  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>é usado para identificar as interfaces de evento que uma classe expõe para clientes do modelo de objeto de componente (COM). Essas interfaces devem ser expostas como `InterfaceIsIDispatch` para permitir que clientes COM do Visual Basic 6 receber notificações de eventos. Por padrão, se uma interface não está marcada com o <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo, ele é exposto como uma interface dupla.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicionar ou modificar o <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atributo para que seu valor é definido como InterfaceIsIDispatch para todas as interfaces que são especificadas com o <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe em que uma das interfaces viola a regra.  
  
 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)