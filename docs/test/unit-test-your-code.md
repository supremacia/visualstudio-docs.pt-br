---
title: "Efetuar teste de unidade em seu código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bafabb6755a5d3c8cf8f2b60b67a9dc0d7af9792
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="unit-test-your-code"></a>Teste de unidade de código
Os testes de unidade fornecem aos desenvolvedores e testadores uma maneira rápida de procurar por erros lógicos nos métodos de classes em projetos do [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], do [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] e do [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].  
  
 As ferramentas de testes de unidade incluem:  
  
1.  **Gerenciador de testes.** O Gerenciador de Testes permite realizar testes de unidade e exibir seus resultados. O Gerenciador de Testes pode usar qualquer framework de teste de unidade, incluindo framework de terceiros, que tenha um adaptador para o Explorer.  
  
2.  **Framework de teste de unidade da Microsoft para código gerenciado.** O framework de testes de unidade da Microsoft para código gerenciado é instalado com o Visual Studio e fornece um framework para testar o código .NET.  
  
3.  **Framework de teste de unidade da Microsoft para C++.** O framework de testes de unidade da Microsoft para C++ é instalado com o Visual Studio e fornece um framework para testar o código nativo.  As estruturas do Google Test, Boost.Test e CTest também estão incluídas com o Visual Studio e os adaptadores de terceiros estão disponíveis para estruturas de teste adicionais. Para obter mais informações, consulte [Escrevendo testes de unidade para C/C++](writing-unit-tests-for-c-cpp.md). 
  
4.  **Ferramentas de cobertura de código.** É possível determinar a quantidade de código do produto que seus testes de unidade utilizam com um comando no Gerenciador de Testes.  
  
5.  **Framework de isolamento do Microsoft Fakes.** O framework de isolamento do Microsoft Fakes pode criar classes e métodos substitutos para o código de produção e de sistema que criam dependências do código em teste. Ao implementar os delegados falsos para uma função, você controla o comportamento e a saída do objeto de dependência.  
  
 Você também pode usar o [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) para explorar seu código .NET para gerar dados de teste e um conjunto de testes de unidade. Para cada instrução no código, é gerada uma entrada de teste para executar essa instrução. Uma análise de caso é realizada para cada branch condicional do código.  
  
## <a name="key-tasks"></a>Tarefas-chave  
 Use os tópicos a seguir como auxílio para entender e criar testes de unidades:  
  
|Tarefas|Tópicos associados|  
|-----------|-----------------------|  
|**Guias de início rápido e passo a passo:** use os tópicos a seguir para aprender sobre teste de unidade no Visual Studio a partir de exemplos de código.|-   [Passo a passo: criação e execução de testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Início rápido: desenvolvimento orientado por testes com o gerenciador de testes](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Adição de testes de unidade a aplicativos do C++ existentes](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|  
|**Teste de unidade com o gerenciador de testes:** saiba como o gerenciador de testes pode ajudar a criar testes de unidade mais produtivos e eficientes.|-   [Noções básicas de teste de unidade](../test/unit-test-basics.md)<br />-   [Criação de um projeto de teste de unidade](../test/create-a-unit-test-project.md)<br />-   [Execução de testes de unidade com o gerenciador de testes](../test/run-unit-tests-with-test-explorer.md)<br />-   [Instalação de frameworks de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md)<br />-   [Atualizar teste de IU codificado no Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)|  
|**Código gerenciado de teste de unidade:**|-   [Como escrever testes de unidade para .NET Framework com o framework de teste de unidade da Microsoft para código gerenciado](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Teste de unidade de código C++**|-   [Como escrever testes de unidade para C/C++ com o framework de testes de unidade da Microsoft para C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolamento de testes de unidade**|-   [Isolamento de código em teste com Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Uso da cobertura de código para identificar quais proporções do código do projeto estão sendo testadas usando os testes de unidade:** saiba mais sobre o recurso de cobertura de código das ferramentas de teste do [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)].|-   [Uso da cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Execução de análise de estresse e desempenho usando testes de carga para seus testes de unidade:** você pode criar um teste de carga e adicionar seus testes de unidade a ele para ajudar a isolar os problemas de estresse e desempenho em seu aplicativo.|-   [Teste de Carga (VSTS e TFS)](/vsts/load-test/)|  
|**Definição e aplicação de restrições de qualidade:** você pode criar restrições de qualidade para garantir que os testes sejam executados antes que o código seja verificado para ajudar a garantir a qualidade do código.|-   [Definição e aplicação de restrições de qualidade](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Extensão do tipo de teste de unidade:**você pode adicionar uma funcionalidade aos seus testes que pode não estar no framework de teste de unidade. Por exemplo, é possível adicionar uma propriedade de teste que especifica se um teste deve ser executado como um usuário normal ou não. Ou você pode estender a estrutura para adicionar atributos de linha a um método e usar os dados nessa linha dentro do teste.|Para o código de exemplo de como estender o framework de teste de unidade, confira este [Site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=185591).|  
|**Definição de opções de teste:** por exemplo, você pode especificar onde os resultados dos testes são armazenados.|[Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Descreve o namespace UnitTesting, que fornece atributos, exceções, asserções e outras classes que oferecem suporte a testes de unidade.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Descreve o namespace UnitTesting.Web, que estende o namespace UnitTesting fornecendo suporte para o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e a testes de unidade do serviço Web.  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="videos"></a>Vídeos  
 [Channel 9: teste de unidade dos aplicativos UWP criados com XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Fóruns  
 [Teste de unidade do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="guidance"></a>Diretrizes  
 [Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Testando para entrega contínua com o Visual Studio 2012 – Capítulo 2: Teste de unidade: testando o interior)  
  
### <a name="reference"></a>Referência  
 [Índice de conteúdo para testes de unidade](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## <a name="see-also"></a>Consulte também

[Melhorar a qualidade do código](/visualstudio/test/improve-code-quality)
