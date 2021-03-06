---
title: 'CA1821: Remova finalizadores vazios | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 98aebdcc889cdd3bd2bbe124b00a572e066b0e4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: remover finalizadores vazios
|||  
|-|-|  
|NomeDoTipo|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo implementa um finalizador que está vazio, chama somente o finalizador do tipo base ou chama somente emitidos condicionalmente métodos.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. O coletor de lixo será executado o finalizador antes que ele coleta o objeto. Isso significa que duas coleções será necessárias para coletar o objeto. Um finalizador vazio gera essa sobrecarga adicionado sem nenhum benefício.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Remova o finalizador vazio. Se um finalizador é necessário para depuração, coloque o finalizador todo `#if DEBUG / #endif` diretivas.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima uma mensagem dessa regra. Falha ao suprimir a finalização reduz o desempenho e não fornece nenhuma benefícios.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um finalizador vazio que deve ser removido, um finalizador que deve ser incluído em `#if DEBUG / #endif` diretivas e um finalizador que usa o `#if DEBUG / #endif` diretivas corretamente.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]