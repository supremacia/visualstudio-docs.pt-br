---
title: "CA1034: Tipos aninhados não devem ser visíveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc35514eab2344c086305ec88435ff8a32285e4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: os tipos aninhados não devem ser visíveis
|||  
|-|-|  
|NomeDoTipo|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente contém uma declaração de tipo visível externamente. Tipos protegidos e enumerações aninhadas são isentos dessa regra.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um tipo aninhado é um tipo declarado dentro do escopo de outro tipo. Tipos aninhados são úteis para encapsular os detalhes de implementação privada do tipo recipiente. Usados para essa finalidade, os tipos aninhados não devem ser visíveis externamente.  
  
 Não use tipos aninhados visíveis externamente para agrupamento lógico ou para evitar colisões de nomes; em vez disso, use namespaces.  
  
 Tipos aninhados incluem a noção de acessibilidade de membro, o que alguns programadores não entender claramente.  
  
 Tipos protegidos podem ser usados em subclasses e tipos aninhados em cenários de personalização avançada.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Se você não for do tipo aninhado para ser visível externamente, altere a acessibilidade do tipo. Caso contrário, remova o tipo aninhado de seu pai. Se a finalidade de aninhamento é categorizar o tipo aninhado, use um namespace para criar a hierarquia em vez disso.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]