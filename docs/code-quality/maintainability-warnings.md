---
title: "Avisos de facilidade de manutenção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8d432dab79d5cd88d398a74c352cc9d34c8b4f2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção
Avisos de facilidade de manutenção suporte à manutenção de biblioteca e o aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA1500: os nomes de variável não devem corresponder aos nomes de campo](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Um método de instância declara um parâmetro ou uma variável local cujo nome corresponda a um campo de instância do tipo declarativo, que leva a erros.|  
|[CA1501: evitar herança excessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter.|  
|[CA1502: evitar complexidade excessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais.|  
|[CA1504: examinar nomes de campo confusos](../code-quality/ca1504-review-misleading-field-names.md)|O nome de um campo de instância começa com "s _", ou o nome de um estático (compartilhado no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo começa com "m _".|  
|[CA1505: evitar código que não possa ser mantido](../code-quality/ca1505-avoid-unmaintainable-code.md)|Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design.|  
|[CA1506: evitar acoplamento de classes excessivo](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.|  
  
## <a name="see-also"></a>Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)