---
title: Analisar dados de uso da CPU (C++) | Microsoft Docs
ms.custom: 
ms.date: 12/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
f1_keywords: 
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7540203c395d51d6372aad908ec028180f41bd7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="analyze-cpu-usage-data-in-visual-studio-c"></a>Analisar dados de uso da CPU no Visual Studio | Microsoft Docs (C++)

O Visual Studio fornece muitos recursos poderosos para ajudar a analisar problemas de desempenho em seu aplicativo. Este tópico fornece uma maneira rápida de conhecer alguns dos recursos básicos. Aqui, vamos examinar a ferramenta para identificar os gargalos de desempenho devido ao alto uso da CPU. As Ferramentas de Diagnóstico têm suporte para desenvolvimento de .NET no Visual Studio, incluindo o ASP.NET e para desenvolvimento nativo/C++.

O Hub de diagnósticos oferece várias outras opções para executar e gerenciar sua sessão de diagnóstico. Se a ferramenta **Uso de CPU** descrita aqui não fornecer os dados que você precisa, as [outras ferramentas de criação de perfil](../profiling/profiling-feature-tour.md) fornecem diferentes tipos de informações que poderão ser úteis. Em muitos casos, o afunilamento de desempenho do aplicativo pode ser causado por algo que não seja a CPU, como memória, interface do usuário de renderização ou tempo de solicitação de rede. O Hub de diagnósticos oferece várias outras opções para registrar e analisar esse tipo de dados.

## <a name="create-a-project"></a>Criar um projeto

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

2. Em **Visual C++**, escolha **Área de Trabalho do Windows** e escolha **Aplicativo de Console do Windows** no painel central.

3. Digite um nome como **Diagnostics_Get_Started_Native** e clique em **OK**.

    O Visual Studio cria o projeto.

4. Em MyDbgApp.cpp, substitua o código a seguir

    ```c++
    int main()
    {
        return 0;
    }
    ```

    por esse código (não remova `#include "stdafx.h"`):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>
    
    //.cpp file code:
    
    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;
    
    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;
    
    int getNumber()
    {
    
        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();
    
        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here  
        // to increase CPU usage 
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }
    
    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;
    
        auto x = getNumber();    
    }
    
    int main()
    {
        std::vector<std::thread> threads;
    
        for (int i = 0; i < 10; ++i) {
    
            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }
    
        for (auto& thread : threads) {
            thread.join();
        }
    
        return 0;
    }
    ```
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Etapa 1: Coletar dados de criação de perfil 
  
1.  Primeiro, defina um ponto de interrupção em seu aplicativo nesta linha de código na função `main`:

    `for (int i = 0; i < 10; ++i) {`

    Defina um ponto de interrupção clicando na medianiz à esquerda da linha de código.

2.  Em seguida, defina um segundo ponto de interrupção no colchete de fechamento no final da função `main`:

     ![Definir pontos de interrupção para criação de perfil](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Definir pontos de interrupção para criação de perfil")

    > [!TIP]
    > Definindo dois pontos de interrupção, você pode limitar a coleta de dados às partes do código que deseja analisar.
  
3.  A janela **Ferramentas de Diagnóstico** já fica visível, a menos que tenha sido desativada. Para abrir a janela novamente, clique em **Depurar/Windows/Mostrar Ferramentas de Diagnóstico**.

4.  Clique em **Depurar/Iniciar Depuração** (ou em **Iniciar** na barra de ferramentas ou em **F5**).

     Quando o aplicativo terminar de ser carregado, a exibição **Resumo** das Ferramentas de Diagnóstico será exibida.

5.  Enquanto o depurador estiver em pausa, habilite a coleta dos dados de Uso da CPU escolhendo **Registrar perfil da CPU** e abra a guia **Uso da CPU**.

     ![Habilitar a criação de perfil da CPU das ferramentas de diagnóstico](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostics Tools Enable CPU Profiling")

     Quando a coleta de dados estiver habilitada, o botão de registro exibe um círculo vermelho.

     Quando você escolhe **Registrar perfil de CPU**, o Visual Studio começará a gravar as funções e quanto tempo elas levam para serem executadas, fornecendo também um gráfico de linha do tempo que você pode usar para se concentrar em segmentos específicos da sessão de amostragem. Você só pode exibir os dados coletados quando seu aplicativo é interrompido no ponto de interrupção.

6.  Pressione F5 para executar o aplicativo até o segundo ponto de interrupção.

     Agora, você tem dados de desempenho do aplicativo especificamente para a região do código que é executada entre os dois pontos de interrupção.

     O criador de perfil começa a preparar os dados de thread. Aguarde sua conclusão.
  
     A ferramenta de Uso de CPU exibe o relatório na guia **Uso da CPU**.

     Neste ponto, você pode começar a analisar os dados.

## <a name="Step2"></a> Etapa 2: Analisar os dados de uso da CPU

Recomendamos que você comece a analisar os dados examinando a lista de funções em Uso da CPU, identificando as funções que fazem a maior parte do trabalho e, em seguida, fazendo uma análise mais detalhada de cada uma.

1. Na lista de funções, examine as funções que fazem a maior parte do trabalho.

     ![Guia Uso da CPU da Ferramentas de Diagnóstico](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > As funções são listadas em ordem, começando com as que fazem a maior parte do trabalho (elas não ficam na ordem de chamada). Isso ajuda a identificar rapidamente as funções com execução mais longa.

2. Na lista de função, clique duas vezes na função `getNumber`.

    Quando você clica duas vezes na função, a exibição **Chamador/Computador Chamado** é aberta no painel esquerdo. 

    ![Exibição Chamador/Computador Chamado da Chamada das Ferramentas de Diagnóstico](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    Nesta exibição, a função selecionada aparece no título e na caixa **Função Atual** (`getNumber`, neste exemplo). A função que chamou a função atual é mostrada à esquerda em **Função Chamadora** e todas as funções chamadas pela função atual são mostradas na caixa **Funções Chamadas** à direita. (Você pode selecionar cada uma das caixas para alterar a função atual.)

    Essa exibição mostra o tempo total (ms) e o percentual do tempo de execução geral do aplicativo que a função levou para ser concluída.

    **Corpo da Função** também mostra a quantidade total de tempo (e o percentual de tempo) gasta no corpo da função, excluindo o tempo gasto nas funções chamadoras e chamadas. (Nesta ilustração, 119 de 43602 ms foram gastos no corpo da função e o tempo restante foi gasto em outro código chamado por essa função). Os valores reais serão muito diferentes dependendo do seu ambiente.

    > [!TIP]
    > Valores altos em **Corpo da Função** podem indicar um afunilamento de desempenho dentro da própria função.

## <a name="next-steps"></a>Próximas etapas

- [Analisar o uso de memória](../profiling/memory-usage.md)para identificar gargalos de desempenho.
- [Analisar o uso da CPU](../profiling/cpu-usage.md) para obter informações mais detalhadas sobre a ferramenta de uso de CPU.
- Analise o uso da CPU sem um depurador conectado ou direcionando um aplicativo em execução. Para saber mais, confira [Coletar dados de criação de perfil sem depuração](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) em [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Consulte também  

 [Criação de perfis no Visual Studio](../profiling/index.md)  
 [Tour pelos recursos de criação de perfil](../profiling/profiling-feature-tour.md)
