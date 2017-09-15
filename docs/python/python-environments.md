---
title: Ambientes do Python no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/25/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e48ebcafaca37505dbcc92bce682d0c6169004e1
ms.openlocfilehash: fa8a7616fe88f024ab299e5d115b66f8656e7cb3
ms.contentlocale: pt-br
ms.lasthandoff: 07/26/2017

---

# <a name="python-environments"></a>Ambientes do Python

O Python no Visual Studio facilita o gerenciamento de vários ambientes do Python e a mudança entre eles em diferentes projetos. 

Observação: se você não estiver familiarizado com o Python no Visual Studio, consulte os tópicos a seguir primeiro, uma vez que esta discussão se baseia neles:

- [Trabalhando com o Python no Visual Studio](python-in-visual-studio.md)
- [Instalando o suporte do Python no Visual Studio](installation.md)

Um *ambiente* do Python, no qual você sempre executa o código dele, consiste em um interpretador, uma biblioteca (normalmente a Biblioteca Padrão do Python) e um conjunto de pacotes instalados. Juntos, esses componentes determinam quais constructos de linguagem e qual sintaxe são válidos, qual funcionalidade do sistema operacional pode ser acessada e quais pacotes podem ser usados.

No Visual Studio, um ambiente também inclui um banco de dados do IntelliSense para as bibliotecas de um ambiente, de modo que digitar uma instrução como `import` no editor do Visual Studio exibe automaticamente uma lista das bibliotecas disponíveis, bem como os módulos dentro dessas bibliotecas.

Muitas vezes, os desenvolvedores usam apenas um único ambiente global do Python. Outros desenvolvedores, no entanto, precisam gerenciar vários ambientes globais, ambientes específicos do projeto e ambientes virtuais, conforme explicado neste tópico:

- [Selecionando e instalando interpretadores do Python](#selecting-and-installing-python-interpreters)
- [Gerenciando ambientes do Python no Visual Studio](#managing-python-environments-in-visual-studio)
- [Ambientes globais](#global-environments)
- [Ambientes específicos ao projeto](#project-specific-environments)
- [Ambientes virtuais](#virtual-environments)
- [Gerenciando os pacotes necessários](#managing-required-packages)
- [Caminhos de pesquisa](#search-paths)

Para obter um vídeo de introdução, assista a [Deep Dive: Python Interpreters](https://youtu.be/KY1GEOo3qy0) (Aprofundamento: Interpretadores do Python)(youtube.com, 13min27s).

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>Selecionando e instalando interpretadores do Python

Com exceção do Visual Studio 2017, o suporte do Python não é fornecido com um interpretador do Python; portanto, é necessário instalar um dos interpretadores a seguir para executar o código. Em geral, o Visual Studio detecta os interpretadores recém-instalados automaticamente e configura um ambiente para cada. Caso ele não detecte um ambiente instalado, confira [Criando um ambiente para um interpretador existente](#creating-an-environment-for-an-existing-interpreter).

| Interpretador | Descrição | 
| --- | --- | 
| [CPython](https://www.python.org/) | O interpretador “nativo” e mais usado, disponível em versões de 32 e 64 bits (o recomendado é 32 bits). Inclui os últimos recursos de linguagem, a compatibilidade máxima com pacotes do Python, suporte de depuração completo e interoperabilidade com o [IPython](http://ipython.org/). Consulte também: [Devo usar o Python 2 ou 3?](http://wiki.python.org/moin/Python2orPython3) |
| [IronPython](https://github.com/IronLanguages/main) | Uma implementação do .NET do Python, disponível em versões de 32 e 64 bits, que fornece interoperabilidade do C#/F#/Visual Basic, acesso às APIs do .NET, depuração padrão do Python (mas não a depuração de modo misto do C++) e a depuração mista do IronPython/C#. No entanto, o IronPython não dá suporte a ambientes virtuais. | 
| [Anaconda](https://www.continuum.io) | Uma plataforma aberta de ciência de dados do Python, além de incluir a última versão do CPython e a maioria dos pacotes difíceis de serem instalados. Recomendamos usá-la, caso você esteja indeciso sobre qual plataforma deverá usar. |
| [PyPy](http://www.pypy.org/) | Uma implementação JIT de rastreamento de alto desempenho do Python que é boa para programas de execução longa e situações em que é possível identificar problemas de desempenho, mas em que não é possível encontrar outras resoluções. Funciona com o Visual Studio, mas com suporte limitado para recursos de depuração avançados. |
| [Jython](http://www.jython.org/) | Uma implementação do Python na JVM (Máquina Virtual Java). Semelhante ao IronPython, o código em execução no Jython pode interagir com classes e bibliotecas Java, mas poderá não usar várias bibliotecas destinadas ao CPython. Funciona com o Visual Studio, mas com suporte limitado para recursos de depuração avançados. |

Para os desenvolvedores que desejam fornecer novas formas de detecção para ambientes do Python, consulte [Detecção para ambiente da PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="managing-python-environments-in-visual-studio"></a>Gerenciando ambientes do Python no Visual Studio

Para abrir a janela Ambientes do Python, siga um destes procedimentos:

1. Selecione o comando de menu **Exibir > Outras Janelas > Ambientes do Python**.
1. Clique com o botão direito do mouse em **Ambientes do Python** de um projeto no Gerenciador de Soluções e selecione **Exibir Todos os Ambientes do Python**:

    ![Comando Exibir Todos os Ambientes no Gerenciador de Soluções](media/environments-view-all.png)
    
Em ambos os casos, a janela Ambientes do Python é exibida como uma guia irmã do Gerenciador de Soluções:

![Janela Ambientes do Python](media/environments-default-view.png)

O exemplo acima mostra que o Python 3.4 (CPython de 32 bits) é instalado junto com as versões de 32 e 64 bits do IronPython 2.7. Neste caso, o ambiente padrão em negrito é o Python 3.4, que é usado para os novos projetos. Se não vir nenhum ambiente listado, isso significa que você instalou as Ferramentas Python para o Visual Studio no Visual Studio 2015 ou anterior, mas ainda não instalou um interpretador do Python (consulte [Selecionando e instalando interpretadores do Python](#selecting-and-installing-python-interpreters) acima). 

> [!Tip]
> Quando a janela **Ambientes do Python** for estreita, conforme mostrado acima, os ambientes serão listados na parte superior e as várias guias na parte inferior. No entanto, expandir a janela o suficiente muda para uma exibição ampla com a qual você talvez considere mais conveniente trabalhar.
>
> ![Exibição expandida da janela Ambientes do Python](media/environments-expanded-view.png)

> [!Note]
> Embora o Visual Studio respeite a opção de pacotes de site do sistema, ele não fornece uma maneira de alterá-lo no próprio Visual Studio.

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Criando um ambiente para um interpretador existente

O Visual Studio normalmente localiza um interpretador Python instalado verificando o registro (seguindo o registro [PEP 514 - Python no registro do Windows](https://www.python.org/dev/peps/pep-0514/)). No entanto, o Visual Studio pode não localizá-lo se o interpretador estiver instalado de maneira não padrão. Nesses casos, é possível apontar o Visual Studio diretamente para o interpretador da seguinte maneira:

1. Selecione **+ Personalizado...** na Janela Ambientes, o que cria um novo ambiente e abre a guia [**Configurar**](#configure-tab) descrita abaixo.

    ![Exibição padrão de um novo ambiente personalizado](media/environments-custom-1.png)

1. Insira um nome para o ambiente no campo **Descrição**.
1. Insira ou procure o caminho do interpretador no campo **Caminho do prefixo**.
1. Selecione **Detecção Automática** para que o Visual Studio preencha os campos restantes ou preencha-os manualmente.
1. Selecione **Aplicar** para salvar o ambiente.
1. Se precisar remover o ambiente, selecione o comando **Remover** na guia **Configurar**. Ambientes detectados automaticamente não oferecem essa opção. Confira a próxima seção para obter mais informações.

### <a name="moving-an-existing-interpreter"></a>Mover um interpretador existente

Se você mover um interpretador existente para um novo local no sistema de arquivos, o Visual Studio não detectará automaticamente a alteração. As etapas manuais são necessárias para atualizar a lista na janela do Ambiente:

- Se você criou originalmente um ambiente para esse interpretador, edite o ambiente para apontar para o novo local.

- Se o ambiente foi detectado automaticamente originalmente, ele foi instalado no computador com um programa de instalador distinto que criou as entradas de registro que o Visual Studio examina. Nesse caso, primeiro restaure o interpretador do Python para o local original. Em seguida, desinstale-o usando o instalador, que limpa as entradas do registro. Em seguida, reinstale o interpretador no local desejado. Reinicie o Visual Studio e ele deverá detectar automaticamente o novo local. Esse processo garante que quaisquer outros efeitos colaterais do instalador sejam aplicados corretamente.

### <a name="overview-tab"></a>Guia Visão Geral

Fornece informações básicas e comandos para o ambiente:

![Guia Visão Geral de Ambientes do Python](media/environments-overview-tab.png)

| Comando | Descrição |
| --- | --- |
| Tornar este ambiente padrão para novos projetos | Definir o ambiente ativo, o que pode fazer com que o Visual Studio pare de responder brevemente enquanto ele carrega o banco de dados do IntelliSense. Ambientes com muitos pacotes podem parar de responder por um período maior. |
| Visitar o site do distribuidor | Abre um navegador para a URL fornecida para a distribuição de Python. Python 3. x, por exemplo, vai para python.org. |
| Abrir a janela interativa | Abre a [janela interativa (REPL)](interactive-repl.md) para esse ambiente dentro do Visual Studio, aplicando quaisquer [scripts de inicialização (veja abaixo)](#startup-scripts). |
| Usar o modo interativo do IPython | Quando definido, abre a janela interativa com IPython por padrão. Isso habilita os gráficos embutidos e a sintaxe estendida do IPython como `name?` para exibir a ajuda e `!command` para comandos shell. Essa opção é recomendada quando estiver usando uma distribuição Anaconda, pois ela requer pacotes extras. Para obter mais informações, consulte [Usando o IPython na Janela Interativa](interactive-repl-ipython.md). |
| Abrir no PowerShell | Inicia o interpretador em uma janela de comando do PowerShell. |
| (Links de pasta) | Fornecem acesso rápido à pasta de instalação do ambiente, o interpretador python.exe e o interpretador pythonw.exe. O primeiro abre no Windows Explorer, os dois últimos abrem uma janela do console. |

#### <a name="startup-scripts"></a>Scripts de inicialização

Como você janelas interativas no fluxo de trabalho diário, provavelmente desenvolverá funções auxiliares que você usa regularmente. Por exemplo, você pode criar uma função que abre um DataFrame no Excel e, em seguida, salvar esse código como um script de inicialização para que ele esteja sempre disponível na janela interativa.

Os scripts de inicialização contêm o código que a janela interativa carrega e executa automaticamente, incluindo importações, definições de função e literalmente qualquer outra coisa. Esses scripts são referenciados de duas maneiras:

1. Quando você instala um ambiente, o Visual Studio cria uma pasta `Documents\Visual Studio 2017\Python Scripts\<environment>` em que &lt;environment&gt' corresponde ao nome do ambiente. Você pode navegar facilmente para a pasta específica do ambiente com o comando **Explorar scripts interativos**. Quando você inicia a janela interativa para esse ambiente, ela carrega e executa qualquer arquivo `.py` que for encontrado aqui em ordem alfabética.

1. O controle **Scripts** na guia **Ferramentas > Opções > Ferramentas do Python > Janelas Interativas** (consulte [Opções de janelas interativas](options.md#interactive-windows-options)) destina-se a especificar uma pasta adicional para os scripts de inicialização que estão carregados e são executados em todos os ambientes. No entanto, esse recurso não funciona no momento.


### <a name="configure-tab"></a>Guia Configurar

Se for mostrada, conterá detalhes, conforme descrito na tabela abaixo. Se essa guia não estiver presente, isso significa que o Visual Studio está gerenciando todos os detalhes automaticamente.

![Guia Configurar de Ambientes do Python](media/environments-configure-tab.png)

| Campo | Descrição |
| --- | --- |
| **Descrição** | O nome a ser fornecido para o ambiente. |
| **Caminho do prefixo** | A localização da pasta base do interpretador. Ao preencher esse valor e clicar em **Detecção Automática**, o Visual Studio tenta preencher os outros campos para você. |
| **Caminho do interpretador** | O caminho para o executável do interpretador, normalmente, o caminho do prefixo seguido por `python.exe` |
| **Interpretador de janela** | O caminho para o executável que não é de console, geralmente, o caminho do prefixo seguido por `pythonw.exe`. |
| **Caminho da biblioteca** | Especifica a raiz da biblioteca padrão, mas esse valor poderá ser ignorado se o Visual Studio conseguir solicitar um caminho mais preciso do interpretador. |
| **Versão da linguagem** | Selecionada no menu suspenso. |
| **Arquitetura** | Normalmente, detectada e preenchida automaticamente; caso contrário, especifica 32 ou 64 bits. |
| **Variável de ambiente do caminho** | A variável de ambiente que o interpretador usa para encontrar caminhos de pesquisa. O Visual Studio altera o valor da variável ao iniciar o Python, para que ela contenha os caminhos de pesquisa do projeto. Normalmente, essa propriedade deve ser definida como `PYTHONPATH`, mas alguns interpretadores usam outro valor. |

### <a name="pip-tab"></a>Guia PIP

Gerencia os pacotes instalados no ambiente, permitindo também pesquisar e instalar novos (incluindo as dependências). A pesquisa filtra seus pacotes instalados no momento e [PyPI](https://pypi.python.org). Também é possível inserir diretamente qualquer comando `pip install` na caixa de pesquisa, incluindo sinalizadores como `--user` ou `--no-deps`.

![Guia PIP de Ambientes do Python](media/environments-pip-tab.png)

Instalar um pacote cria subpastas dentro da pasta `Lib` do ambiente no sistema de arquivos. Por exemplo, se você tiver Python 3.6 instalados em `c:\Python36`, os pacotes são instalados em `c:\Python36\Lib`, se você tiver o Anaconda3 instalado em `c:\Program Files\Anaconda3`, os pacotes serão instalados em `c:\Program Files\Anaconda3\Lib`.

No último caso, como o ambiente está localizado em uma área protegida do sistema de arquivos, `c:\Program Files`, o Visual Studio deve executar `pip install` com privilégios elevados para permitir que ele crie subpastas do pacote. Quando a elevação é necessária, o Visual Studio exibe o prompt, "Podem ser necessários privilégios de administrador para instalar, atualizar ou remover pacotes para esse ambiente":

![Solicitação de elevação para a instalação do pacote](media/environments-pip-elevate.png)

**Elevar agora** concede privilégios administrativos para executar o PIP para uma única operação, sujeita também a qualquer prompt de permissão do sistema operacional. Selecionar **Continuar sem Privilégios de administrador** tenta instalar o pacote, mas o PIP falha ao tentar criar pastas com uma saída como “erro: não foi possível criar 'C:\Arquivos de Programas\Anaconda3\Lib\site-packages\png.py': permissão negada”.

Selecionar **Sempre elevar ao instalar o u remover pacotes** impede que a caixa de diálogo apareça para o ambiente em questão. Para fazer a caixa de diálogo aparecer novamente, vá para **Ferramentas > Opções > Ferramentas do Python > Geral** e selecione o botão **Redefinir todas as caixas de diálogo permanentemente ocultas**. 

Nessa mesma guia de opções, você também pode selecionar **Sempre executar o PIP como administrador** para suprimir a caixa de diálogo para todos os ambientes. Consulte [Opções – guia Geral](options.md#general-options).


### <a name="intellisense-tab"></a>Guia IntelliSense

Mostra o status atual do banco de dados de preenchimento do IntelliSense:

![Guia IntelliSense de Ambientes do Python](media/environments-intellisense-tab.png)

O banco de dados contém metadados para todas as bibliotecas do ambiente, melhora a velocidade do IntelliSense e reduz o uso de memória. Quando o Visual Studio detecta um novo ambiente (ou você adiciona um), ele começa a compilar o banco de dados automaticamente, analisando os arquivos de origem da biblioteca. Esse processo pode levar de um minuto a uma hora ou mais, dependendo do que está instalado. (O Anaconda, por exemplo, é fornecido com várias bibliotecas e leva algum tempo para compilar o banco de dados.) Depois de concluído, você obtém um IntelliSense detalhado não precisa atualizar o banco de dados novamente (com o botão **Atualizar Banco de Dados**) quando instalar mais bibliotecas.

As bibliotecas para as quais os dados não foram compilados serão marcadas com um **!**; se o banco de dados de um ambiente não estiver concluído, um **!** também é exibido ao lado da lista do ambiente principal.

## <a name="global-environments"></a>Ambientes globais

Ambientes globais (ou de todo o sistema) estão disponíveis para todos os projetos em um computador. Geralmente, o Visual Studio detecta ambientes globais automaticamente e eles podem ser exibidos na janela Ambientes do Python. Caso contrário, é possível adicionar um manualmente, conforme descrito anteriormente em [Gerenciando ambientes do Python no Visual Studio](#managing-python-environments-in-visual-studio).

O Visual Studio usa o ambiente padrão para todos os novos projetos para execução, depuração, verificação de sintaxe, exibição de preenchimentos de importação e membro e todas as outras tarefas que exigem um ambiente. Alterar o ambiente padrão afeta todos os projetos que não tiveram um [ambiente específico ao projeto](#project-specific-environments) adicionado, conforme descrito a seguir.

## <a name="project-specific-environments"></a>Ambientes específicos ao projeto

Ambientes específicos ao projeto garantem que um projeto sempre é executado em um ambiente específico, ignorando o ambiente global padrão. Por exemplo, se o ambiente global padrão for o CPython, mas um projeto exigir o IronPython e determinadas bibliotecas que não estão instaladas no ambiente global, um ambiente específico ao projeto será necessário.

Os ambientes de projeto são listados no Gerenciador de Soluções, no nó Ambientes do Python. A entrada em negrito está ativa no momento e o Visual Studio a utiliza para a depuração, preenchimentos de importação e membro, verificação de sintaxe e todas as outras tarefas que exigem um ambiente:

![Ambientes de projeto exibidos no Gerenciador de Soluções](media/environments-project.png)

Para ativar outro ambiente para o projeto, clique com o botão direito do mouse nesse ambiente e selecione **Ativar Ambiente**.

Qualquer ambiente global pode ser adicionado como um ambiente de projeto clicando com o botão direito do mouse em **Ambientes do Python** e selecionando **Adicionar/Remover Ambientes do Python...**. Na lista exibida, é possível marcar ou desmarcar os ambientes que estão disponíveis no projeto.

![Caixa de diálogo Adicionar/Remover Ambientes do Python](media/environments-add-remove.png)

No Gerenciador de Soluções, também é possível expandir o ambiente para mostrar seus pacotes instalados (aqueles que podem ser importados e usados no código quando o ambiente está ativo):

![Pacotes do Python para um ambiente no Gerenciador de Soluções](media/environments-installed-packages.png)

Para instalar novos pacotes, clique com o botão direito do mouse no ambiente, selecione **Instalar Pacote do Python...** e insira o nome do pacote desejado. Os pacotes (e as dependências) são baixados no [PyPI (Índice do Pacote do Python)](https://pypi.python.org/pypi), no qual você também pode pesquisar os pacotes disponíveis. A barra de status e a janela de saída do Visual Studio mostram informações sobre a instalação. Para desinstalar um pacote, clique com o botão direito do mouse nele e selecione **Remover**.

> [!Note]
> Atualmente, o suporte ao gerenciamento de pacotes do Python está em desenvolvimento pela equipe principal de desenvolvimento do Python. As entradas exibidas podem não ser precisas e a instalação e desinstalação podem não ser confiáveis nem estar disponíveis. O Visual Studio usa o gerenciador de pacotes do PIP, se disponível, e o baixa e o instala quando necessário. O Visual Studio também pode usar o gerenciador de pacotes easy_install. Os pacotes instalados usando o PIP ou easy_install por meio da linha de comando também são exibidos.

> [!Tip]
> Uma situação comum em que o PIP não conseguirá instalar um pacote é quando o pacote inclui o código-fonte para componentes nativos em arquivos `*.pyd`. Sem a versão necessária do Visual Studio instalada, o PIP não pode compilar esses componentes. A mensagem de erro exibida nessa situação é `error: Unable to find vcvarsall.bat`. O `easy_install` consegue baixar os binários pré-compilados e é possível baixar um compilador adequado para versões mais antigas do Python em [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para obter mais detalhes, consulte [Como lidar com o problema “Não é possível localizar vcvarsallbat”](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) no blog da equipe das Ferramentas Python.


## <a name="virtual-environments"></a>Ambientes Virtuais

Como os pacotes instalados em um ambiente global estão disponíveis para todos os projetos que os usam, poderão ocorrer conflitos quando dois projetos exigirem pacotes incompatíveis ou versões diferentes do mesmo pacote. Para evitar conflitos como esse, o Visual Studio fornece a capacidade de criar *ambientes virtuais*, que, normalmente, são específicos a um projeto.

Assim como qualquer outro ambiente do Python, um ambiente virtual consiste em um interpretador do Python, uma biblioteca e um conjunto de pacotes. No entanto, nesse caso, o ambiente virtual usa o interpretador e a biblioteca de um dos ambientes globais (desde que ele dê suporte a ambientes virtuais), mas seus pacotes são separados e isolados do ambiente global e de todos os outros ambientes virtuais. Novamente, esse isolamento evita conflitos e minimiza a superfície do ambiente virtual ao tamanho aproximado de seus pacotes. 

Para criar um ambiente virtual:

1. Clique com o botão direito do mouse em **Ambientes do Python** no Gerenciador de Soluções e selecione **Adicionar Ambiente Virtual...**, que abre o seguinte:

    ![Criando um ambiente virtual](media/environments-add-virtual-1.png)

1. Especifique um nome para criar o ambiente virtual no caminho do projeto ou um caminho completo para criá-lo em outro lugar. (Para garantir a máxima compatibilidade com outras ferramentas, use apenas letras e números no nome.)

1. Selecione um ambiente global como o interpretador base e clique em **Criar**. Se os pacotes `pip` e `virtualenv` ou `venv` não estiverem disponíveis, eles serão baixados e instalados.

    Se o caminho fornecido for um ambiente virtual existente, o interpretador base será detectado e o botão Criar será alterado para **Adicionar**:

    ![Adicionando um ambiente virtual existente](media/environments-add-virtual-2.png)

Um ambiente virtual existente também pode ser adicionado clicando com o botão direito do mouse em **Ambientes do Python** no Gerenciador de Soluções e selecionando **Adicionar Ambiente Virtual Existente...**. O Visual Studio detecta o interpretador base automaticamente usando o arquivo `orig-prefix.txt` no diretório `lib` do ambiente.

Depois que um ambiente virtual é adicionado ao projeto, ele é exibido na janela **Ambientes do Python** e é possível ativá-lo como qualquer outro ambiente, além de gerenciar seus pacotes. Clicar com o botão direito do mouse e selecionar **Remover** remove a referência ao ambiente ou exclui o ambiente e todos os seus arquivos em disco (mas não o interpretador base).

Observe que uma desvantagem dos ambientes virtuais é que eles contêm caminhos de arquivo embutidos em código e, portanto, não podem ser facilmente compartilhados nem transportados para outros computadores de desenvolvimento. Felizmente, é possível usar o arquivo `requirements.txt`, conforme descrito na próxima seção.

## <a name="managing-required-packages"></a>Gerenciando os pacotes necessários

Se você estiver compartilhando um projeto com outras pessoas, usando um sistema de build ou pretender [publicá-lo no Microsoft Azure](template-azure-cloud-service.md), precisará especificar os pacotes externos exigidos por ele. A abordagem recomendada é usar um [arquivo requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) que contém uma lista de comandos do PIP que instala as versões necessárias dos pacotes dependentes.

Tecnicamente, qualquer nome de arquivo pode ser usado para acompanhar os requisitos (usando `-r <full path to file>` durante a instalação de um pacote), mas o Visual Studio fornece suporte específico para `requirements.txt`:

- Se você carregou um projeto que contém `requirements.txt` e deseja instalar todos os pacotes listados nesse arquivo, clique com o botão direito do mouse no projeto e selecione **Instalar de requirements.txt**:

    ![Instalar de requirements.txt](media/environments-requirements-txt-install.png)

- Quando tiver todos os pacotes necessários instalados em um projeto, é possível clicar com o botão direito do mouse no projeto, no Gerenciador de Soluções e selecionar **Gerar requirements.txt** para criar o arquivo necessário. Se o arquivo já existir, será exibido um prompt para como atualizá-lo:

    ![Opções de atualização de requirements.txt](media/environments-requirements-txt-replace.png)

    - **Substituir todo o arquivo** remove todos os itens, comentários e opções existentes.
    - **Atualizar as entradas existentes** detecta os requisitos do pacote e atualiza os especificadores de versão para que eles correspondam à versão instalada.
    - **Atualizar e adicionar entradas** atualiza todos os requisitos encontrados e adiciona todos os outros pacotes ao final do arquivo.

Como os arquivos `requirements.txt` se destinam a congelar os requisitos do projeto, todos os pacotes instalados são escritos com versões precisas. Usar versões precisas garante que você possa reproduzir facilmente seu ambiente em outro computador. Os pacotes serão incluídos, mesmo se eles foram instalados com um intervalo de versão, como uma dependência de outro pacote ou com um instalador que não seja o PIP.

Se existir um arquivo ` requirements.txt` ao adicionar um novo ambiente virtual, a caixa de diálogo **Adicionar Ambiente Virtual** exibirá uma opção para instalar os pacotes automaticamente, facilitando a recriação de um ambiente em outro computador:

![Criar um ambiente virtual com requirements.txt](media/environments-requirements-txt.png)

Se um pacote não puder ser instalado pelo PIP e for exibido em um arquivo `requirements.txt`, toda a instalação falhará. Nesse caso, edite manualmente o arquivo para excluir esse pacote ou use as [opções do PIP](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) para se referir a uma versão instalável do pacote. Por exemplo, você pode preferir usar [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) para compilar uma dependência e adicionar o opção `--find-links <path>` ao `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>Caminhos de pesquisa

Com o uso típico do Python, a variável de ambiente `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fornece o caminho de pesquisa padrão para arquivos de módulo. Ou seja, quando você usa uma instrução `import <name>`, o Python primeiro pesquisa seus módulos internos em busca de um nome correspondente e, em seguida, pesquisa a pasta que contém o código do Python que está sendo executado e o “caminho de pesquisa do módulo”, conforme definido pela variável de ambiente aplicável. (Consulte [O caminho de pesquisa do módulo](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) e [Variáveis de ambiente](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) na documentação básica do Python.)

No entanto, a variável de ambiente do caminho de pesquisa é ignorada pelo Visual Studio, mesmo quando ela foi configurada para todo o sistema. Ela é precisamente ignorada, na verdade, *porque* é definida para todo o sistema e, portanto, gera algumas perguntas que não podem ser respondidas automaticamente: os módulos referenciados são destinados ao Python 2.7 ou ao Python 3.3? Eles substituirão os módulos da biblioteca padrão? O desenvolvedor está ciente desse comportamento ou essa é uma tentativa de sequestro mal-intencionada?

Portanto, o suporte do Python no Visual Studio fornece um meio para especificar caminhos de pesquisa diretamente nos projetos e ambientes. Os caminhos de pesquisa são passados como o valor `PYTHONPATH` (ou equivalente) durante a depuração ou execução do script no Visual Studio. Ao adicionar caminhos de pesquisa, o Visual Studio inspeciona as bibliotecas nessas localizações e compila bancos de dados do IntelliSense para elas (a criação do banco de dados pode demorar algum tempo, dependendo do número de bibliotecas).

Para adicionar um caminho de pesquisa, clique com o botão direito do mouse no item **Caminhos de Pesquisa** no Gerenciador de Soluções, selecione **Adicionar Pasta ao Caminho de Pesquisa...** e selecione a pasta a ser incluída. Esse caminho é usado para qualquer ambiente associado ao projeto.

Os arquivos com uma extensão `.zip` ou `.egg` também podem ser adicionados como caminhos de pesquisa selecionando **Adicionar Arquivo Morto Zip para Caminho de Pesquisa...**. Assim como ocorre com pastas, o conteúdo desses arquivos é examinado e disponibilizado para o IntelliSense.

> [!Note]
> É possível adicionar um caminho de pesquisa aos módulos do Python 2.7 enquanto você estiver usando o Python 3.3 e é possível ver erros como resultado.

Se estiver usando regularmente os mesmos caminhos de pesquisa e o conteúdo não for alterado com frequência, poderá ser mais eficiente instalá-lo na pasta de pacotes do site. Em seguida, ele é analisado e armazenado no banco de dados do IntelliSense, sempre é associado ao ambiente pretendido e não exige um caminho de pesquisa a ser adicionado para cada projeto.
