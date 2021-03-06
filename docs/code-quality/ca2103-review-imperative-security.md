---
title: "CA2103: Revisar segurança obrigatória | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 051c94905e8d62d39ef837b6ef2520f345b8ca56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2103-review-imperative-security"></a>CA2103: revisar segurança obrigatória
|||  
|-|-|  
|NomeDoTipo|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Segurança obrigatória usa objetos gerenciados para especificar permissões e ações de segurança durante a execução de código, em comparação comparada a segurança declarativa, que usa atributos para armazenar permissões e ações nos metadados. Segurança obrigatória é muito flexível, porque você pode definir o estado de um objeto de permissão e selecione as ações de segurança usando as informações que não estão disponíveis até o tempo de execução. Junto com que a flexibilidade vem o risco de que as informações de tempo de execução que você pode usar para determinar que o estado de uma permissão não permanecem inalteradas desde que a ação está em vigor.  
  
 Use a segurança declarativa sempre que possível. As solicitações declarativas são mais fáceis de entender.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Examine as demandas de segurança obrigatória para certificar-se de que o estado da permissão não se baseia em informações que podem ser alterados desde que a permissão está sendo usada.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se a permissão não depende de alteração de dados. No entanto, é melhor alterar a demanda fundamental para seu equivalente declarativa.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Dados e modelagem](/dotnet/framework/data/index)