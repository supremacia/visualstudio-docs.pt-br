---
title: Usando regras de desempenho para analisar dados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 09b7ca87e18a3c12a47c95ff8a0f4f5867b641e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-performance-rules-to-analyze-data"></a>Usando regras de desempenho para analisar dados
Os avisos de desempenho das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] indicam problemas em um aplicativo analisado que podem causar lentidão na execução do programa. Os avisos também podem indicar que talvez seja necessário alterar os métodos de coleta para coletar dados mais úteis. Avisos de desempenho são gerados automaticamente em uma sessão de criação de perfil. Os avisos são exibidos na janela **Lista de Erros** quando um arquivo de dados de criação de perfil está aberto no Visual Studio. Na janela **Lista de Erros**, é possível localizar o código-fonte do problema e exibir informações detalhadas sobre o erro, por exemplo, como resolvê-lo. Também é possível desabilitar avisos nos quais você não está interessado.  
  
> [!NOTE]
>  Os avisos de desempenho do criador de perfil são gerados pela análise dinâmica da execução do programa e são independentes dos avisos de Análise de Código. A Análise de Código também pode gerar avisos de desempenho para código gerenciado com base na análise estática do código-fonte. Para obter mais informações, consulte [Analisando a Qualidade do Código Gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) e [Avisos de Desempenho](../code-quality/performance-warnings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como exibir avisos de desempenho](../profiling/how-to-view-performance-warnings.md)  
 Fornece informações sobre como abrir a janela **Lista de Erros** para exibir avisos de desempenho do criador de perfil.  
  
 [Como configurar regras de desempenho](../profiling/how-to-configure-performance-rules.md)  
 Fornece informações sobre como ativar ou desativar avisos de desempenho individuais.  
  
 [Referência de regras de desempenho](../profiling/performance-rules-reference.md)  
 Fornece informações detalhadas sobre os avisos de desempenho do criador de perfil