---
title: "Referência de conjunto de regras de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0bc2b01641c6f6b333ef5323a60672818cc5e7b3
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2018
---
# <a name="code-analysis-rule-set-reference"></a>Referência do conjunto de regras da análise de código

Quando você configurar a análise de código para projetos de código gerenciado no Visual Studio, você verá uma lista dos internas *conjuntos de regras*. Você pode usar qualquer um dos conjuntos de regras padrão, ou você pode personalizar uma regra definida de acordo com seus requisitos de projeto.

## <a name="available-rule-sets"></a>Conjuntos de regras disponíveis

A tabela a seguir lista os conjuntos de regras padrão:

|||
|-|-|
|[Conjunto de regras Todas as Regras](../code-quality/all-rules-rule-set.md)|Esse conjunto de regras contém todas as regras. Executar esse conjunto de regras pode resultar em um grande número de avisos relatados. Use este conjunto de regras para obter uma visão abrangente de todos os problemas em seu código. Isso pode ajudá-lo a decidir qual a regra mais direcionada conjuntos são mais apropriados para execução em seus projetos.|
|[Conjunto de regras básicas de correção para código gerenciado](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Estas regras enfocam erros de lógica e comuns cometidos no uso de APIs do framework. Inclua este conjunto de regras para expandir a lista de avisos relatados pelas regras recomendadas mínimas.|
|[Conjunto de regras básicas de diretrizes de design para código gerenciado](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Estas regras enfocam a imposição de práticas recomendadas para tornar o seu código fácil de entender e usar. Inclua este conjunto se seu projeto incluir código de biblioteca ou se você quiser impor práticas recomendadas para o código de fácil manutenção de regras.|
|[Conjunto de regras de correção estendido para código gerenciado](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Estas regras expandem as regras básicas de correção para maximizar os erros de uso de lógica e do framework que são relatados. É dada ênfase adicional em cenários específicos, como aplicativos móveis e interoperabilidade de COM. Inclua esta regra definir se um desses cenários se aplicar ao seu projeto ou para localizar problemas adicionais no seu projeto.|
|[Conjunto de regras estendidas de diretrizes de design para código gerenciado](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Estas regras expandem as regras de diretriz do design básico para maximizar os problemas de usabilidade e manutenção que são relatados. É dada ênfase adicional diretrizes de nomenclatura. Considere a possibilidade de incluir este conjunto se seu projeto incluir código de biblioteca ou se você quiser impor os mais altos padrões para escrever um código de regras.|
|[Conjunto de regras de globalização para código gerenciado](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Estas regras enfocam os problemas que impedem que os dados em seu aplicativo sejam exibidos corretamente quando usados em diferentes idiomas, localidades e culturas. Inclua esta regra definida se seu aplicativo seja traduzido ou globalizado.|
|[Gerenciado mínimo conjunto de regras para código gerenciado](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Estas regras enfocam os problemas mais críticos em seu código para o qual análise de código é o mais preciso. Essas regras são em pequenas número e eles se destinam apenas à execução em edições limitadas do Visual Studio. Use Minimumrecommendedrules com outras edições do Visual Studio.|
|[Conjunto de regras recomendadas gerenciado para código gerenciado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Estas regras enfocam os problemas mais críticos do código, inclusive falhas potenciais de segurança, falhas de aplicativo e outros erros importantes de lógica e design. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que criar para seus projetos.|
|[Conjunto de regras mínimas misto](../code-quality/mixed-minimum-rules-rule-set.md)|Estas regras enfocam os problemas mais críticos em seus projetos do C++ que dão suporte a Common Language Runtime, inclusive falhas potenciais de segurança e falhas de aplicativo. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que cria para seus projetos em C++ que dão suporte a Common Language Runtime.|
|[Conjunto de regras recomendadas misto](../code-quality/mixed-recommended-rules-rule-set.md)|Estas regras enfocam os problemas mais críticos e comuns em seus projetos do C++ que dão suporte a Common Language Runtime, inclusive falhas potenciais de segurança, falhas de aplicativo e outros erros importantes de lógica e design. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que cria para seus projetos em C++ que dão suporte a Common Language Runtime. |
|[Conjunto de regras mínimas nativo](../code-quality/native-minimum-rules-rule-set.md)|Estas regras enfocam os problemas mais críticos do código nativo, inclusive falhas potenciais de segurança e falhas de aplicativo. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que criar para seus projetos nativos.|
|[Conjunto de regras recomendadas nativo](../code-quality/native-recommended-rules-rule-set.md)|Estas regras enfocam os problemas mais críticos e comuns do código nativo, inclusive falhas potenciais de segurança e falhas de aplicativo. Você deve incluir este conjunto de regras em qualquer conjunto personalizado que criar para seus projetos nativos. |
|[Conjunto de regras de segurança para código gerenciado](../code-quality/security-rules-rule-set-for-managed-code.md)|Esse conjunto de regras contém todas as regras de segurança da Microsoft. Inclua este conjunto de regras para maximizar o número de possíveis problemas de segurança que são relatados.|
