---
title: "Configurando opções de sessão de desempenho geral | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36e27189102fbab8e698320c49bd008adf1eda50
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2018
---
# <a name="setting-general-performance-session-options"></a>Definindo opções de sessão de desempenho geral

Você pode definir o método de coleção e convenções de nomenclatura de dados de criação de perfil para uma sessão de desempenho das Ferramentas de Criação de Perfil do no Visual Studio na página **Geral** da caixa de diálogo Propriedades da sessão de desempenho. Para abrir a caixa de diálogo **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.

## <a name="choosing-data-collection-methods"></a>Escolher os métodos de coleta de dados

Definir o método de coleção base selecionando uma das opções em **Coleção de Perfis**. As opções são descritas seguindo a tabela a seguir:

|||
|-|-|
|**Amostragem**. O método de amostragem coleta informações de perfil em intervalos regulares. Este método é útil para localizar problemas de utilização do processador e é o método sugerido para iniciar a maioria das investigações de desempenho.|- [Coletando estatísticas de desempenho usando amostragem](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentação**. O método de instrumentação injeta em uma cópia de um módulo de código que registra cada entrada, saída e a chamada de função das funções no módulo durante uma geração de perfil de criação de perfil. Este método é útil para coletar informações detalhadas de tempo sobre uma seção do seu código e para compreender o impacto das operações de entrada e saída sobre o desempenho do aplicativo.|- [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Simultaneidade**. O método de simultaneidade coleta dados para cada evento que bloqueia a execução de seu código, como quando um thread aguarda bloqueia o acesso a um recurso de aplicativo para ser liberado. Esse método é útil para analisar aplicativos multi-threaded.|- [Coletando dados de simultaneidade do thread e do processo](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Você pode coletar dados de memória do .NET usando os métodos de amostragem ou instrumentação. Selecione o tipo de dados na **criação de perfil de memória do .NET**.

|||
|-|-|
|**Coletar informações de alocação de objeto do .NET**. Por padrão, os dados incluem o número e tamanho dos objetos alocados. Marque ou desmarque esta caixa de seleção para habilitar ou desabilitar a coleta de dados de memória do .NET.<br /><br /> **Também coletar informações de tempo de vida do objeto .NET**. Marque esta caixa de seleção para incluir dados sobre as gerações de coleta de lixo que foram usados para recuperar os objetos de memória.|- [Coletando a alocação de memória do .NET e os dados de tempo de vida](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|

 Uma página de sessão de criação de perfil aparece quando você começar a criar o perfil de um aplicativo, no qual você pode pausar, retomar e parar criação de perfil.

 ![Página de sessão de criação de perfil](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="setting-profiling-data-file-options"></a>Configurar opções de arquivo de dados de criação de perfil

|||
|-|-|
|**Relatório**. Por padrão, o arquivo de dados (.vsp) de criação de perfil é dado o nome do aplicativo com perfil e está localizado na pasta de solução ou projeto. Uma cadeia de caracteres de data também é acrescentada ao nome e um número incrementado é adicionado aos arquivos de dados que outra forma, teriam nomes duplicados. Você pode alterar essas opções.|- [Como definir opções de nome de arquivo de dados de desempenho](../profiling/how-to-set-performance-data-file-name-options.md)|