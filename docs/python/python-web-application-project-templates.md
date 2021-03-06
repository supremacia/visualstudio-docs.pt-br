---
title: Modelos de aplicativo Web para o Python no Visual Studio | Microsoft Docs
description: "Uma visão geral dos modelos do Visual Studio para aplicativos Web escritos em Python usando as estruturas Bottle, Flask e Django, incluindo configurações de depuração e publicação no Serviço de Aplicativo do Azure."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: b75aae5811fa2410cf169d3401184b8af7ca381d
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="python-web-application-project-templates"></a>Modelos de projeto de aplicativo Web Python

O Python no Visual Studio é compatível com o desenvolvimento de projetos da Web nas estruturas Bottle, Flask e Django por meio de modelos de projeto e um inicializador de depuração que pode ser configurado para manipular várias estruturas. Você também pode usar o modelo genérico **Projeto Web** para outras estruturas, como Pyramid.

O Visual Studio não inclui as estruturas. Você deve instalar as estruturas separadamente, clicando com o botão direito do mouse no projeto e selecionando **Python > Instalar/atualizar estrutura...**.

Quando executado, um projeto criado com base em um modelo (acessado por meio de **Arquivo > Novo > Projeto...**) inicia um servidor Web com uma porta local selecionada aleatoriamente, abre o navegador padrão durante a depuração e permite a publicação direta no Microsoft Azure.

![Novos modelos de projeto Web](media/template-web-new-project.png)

Os modelos do Bottle, Flask e Django incluem um site inicial com algumas páginas e alguns arquivos estáticos. Esse código é suficiente para executar e depurar o servidor localmente (em que algumas configurações precisam ser obtidas do ambiente) e para implantar o Microsoft Azure (em que um objeto [aplicativo WSGI](http://www.python.org/dev/peps/pep-3333/) precisa ser fornecido).

Ao criar um projeto com base em um modelo específico à estrutura, uma caixa de diálogo é exibida para ajudá-lo a instalar os pacotes necessários usando o PIP. Também recomendamos o uso de um [ambiente virtual](selecting-a-python-environment-for-a-project.md#using-virtual-environments) para projetos Web, para que as dependências corretas sejam incluídas durante a publicação do site:

![Caixa de diálogo que instala os pacotes necessários para um modelo de projeto](media/template-web-requirements-txt-wizard.png)

Ao implantar o Serviço de Aplicativo do Microsoft Azure, selecione uma versão do Python como uma [extensão de site](https://aka.ms/PythonOnAppService) e instalar os pacotes manualmente. Além disso, como o Serviço de Aplicativo do Azure **não** instala pacotes automaticamente de um arquivo `requirements.txt` quando implantado por meio do Visual Studio, siga os detalhes de configuração em [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Os Serviços de Nuvem do Microsoft Azure *dá* suporte ao arquivo `requirements.txt`. [Projetos do Serviço de Nuvem do Azure](python-azure-cloud-service-project-template.md) para obter detalhes.

## <a name="debugging"></a>Depuração

Quando um projeto Web for iniciado para depuração, o Visual Studio iniciará o servidor Web localmente e abrirá o navegador padrão nesse endereço e nessa porta. Para especificar opções adicionais, clique com o botão direito do mouse no projeto, selecione **Propriedades** e selecione a guia **Inicializador da Web**:

  ![Propriedades do inicializador da Web para o modelo da Web genérico](media/template-web-launcher-properties.png)

No grupo **Depurar**:

- **Caminhos de Pesquisa**, **Argumentos de Script**, **Argumentos do Interpretador** e **Caminho do Interpretador**: essas opções são as mesmas da [depuração normal](debugging-python-in-visual-studio.md)
- **URL de Inicialização**: especifica a URL que é aberta no navegador. Usa como padrão `localhost`.
- **Número da Porta**: a porta a ser usada se nenhuma for especificada na URL (o Visual Studio seleciona uma automaticamente por padrão). Essa configuração permite substituir o valor padrão da variável de ambiente `SERVER_PORT`, que é usada pelos modelos para configurar a porta na qual o servidor de depuração local escuta.

As propriedades dos grupos **Executar Comando do Servidor** e **Depurar Comando do Servidor** (o último está abaixo do que é mostrado na imagem) determinam como o servidor Web é iniciado. Como muitas estruturas exigem o uso de um script fora do projeto atual, o script pode ser configurado aqui e o nome do módulo de inicialização pode ser passado como um parâmetro.

- **Comando**: pode ser um script do Python (arquivo `*.py`), um nome de módulo (como em `python.exe -m module_name`) ou uma linha de código individual (como em `python.exe -c "code"`). O valor na lista suspensa indica qual desses tipos é pretendido.
- **Argumentos**: esses argumentos são passados na linha de comando após o comando.
- **Ambiente**: uma lista separada por nova linha de pares `NAME=VALUE` que especificam as variáveis de ambiente. Essas variáveis são definidas após todas as propriedades que podem modificar o ambiente, como o número da porta e os caminhos de pesquisa e, portanto, podem substituir esses valores.

Qualquer propriedade de projeto ou variável de ambiente pode ser especificada com a sintaxe do MSBuild, por exemplo: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` é o caminho relativo para o arquivo de inicialização e `{StartupModule}` é o nome importável do arquivo de inicialização. `$(SERVER_HOST)` e `$(SERVER_PORT)` são variáveis de ambiente normais definidas pelas propriedades **URL de Inicialização** e **Número da Porta**, automaticamente ou pela propriedade **Ambiente**.

> [!Note]
> Os valores em **Executar Comando do Servidor** são usados com o comando **Depurar > Iniciar Servidor** ou Ctrl-F5; os valores no grupo **Depurar Comando do Servidor** são usados com o comando **Depurar > Iniciar Servidor de Depuração** ou F5.

### <a name="sample-bottle-configuration"></a>Configuração do Bottle de exemplo

O modelo de **Projeto Web Bottle** inclui um código de texto clichê que faz a configuração necessária. Um aplicativo importado do Bottle pode não incluir esse código; no entanto, nesse caso, as seguintes configurações iniciam o aplicativo usando o módulo `bottle` instalado:

- Grupo **Executar Comando do Servidor**:
  - **Comando**: `bottle` (módulo)
  - **Argumentos**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Grupo **Depurar Comando do Servidor**:
  - **Comando**: `bottle` (módulo)
  - **Argumentos** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

A opção `--reload` não é recomendada ao usar o Visual Studio para depuração.

### <a name="sample-pyramid-configuration"></a>Configuração de exemplo do Pyramid

Atualmente, a melhor forma de criar aplicativos do Pyramid é usando a ferramenta de linha de comando `pcreate`. Quando um aplicativo for criado, ele poderá ser importado usando o modelo [Com base em um código existente do Python](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files). Depois de fazer isso, selecione a personalização **Projeto Web Genérico** para configurar as opções. Essas configurações presumem que o Pyramid está instalado em um ambiente virtual em `..\env`.

- Grupo **Depurar**:
  - **Porta do Servidor**: 6543 (ou o que estiver configurado nos arquivos .ini)

- Grupo **Executar Comando do Servidor**:
  - Comando: `..\env\scripts\pserve-script.py` (script)
  - Argumentos: `Production.ini`

- Grupo **Depurar Comando do Servidor**:
    - Comando: `..\env\scripts\pserve-script.py` (script)
    - Argumentos: `Development.ini`

> [!Tip]
> Provavelmente, você precisa configurar a propriedade **Diretório de Trabalho** do projeto, pois os aplicativos do Pyramid estão normalmente em um nível de diretório mais profundo na parte superior da árvore de origem.

### <a name="other-configurations"></a>Outras configurações

Se você tiver configurações para outra estrutura que gostaria de compartilhar ou se gostaria de solicitar configurações para outra estrutura, abra um [problema no GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Publicando no Serviço de Aplicativo do Azure

Há duas maneiras principais de publicação no Serviço de Aplicativo do Azure. Primeiro, a implantação por meio do controle do código-fonte pode ser usada da mesma forma que em outras linguagens, conforme descrito na [documentação do Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Para publicar diretamente do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Publicar**:

![Comando Publicar em um menu de contexto do projeto](media/template-web-publish-command.png)

Depois de selecionar o comando, um assistente o orientará durante a criação de um site ou importação de configurações de publicação, visualização de arquivos modificados e publicação em um servidor remoto.

Ao criar um site no Serviço de Aplicativo, você precisa instalar o Python e todos os pacotes dos quais o site depende. É possível publicar o site primeiro, mas ele não será executado até que o Python seja configurado.

Para instalar o Python no Serviço de Aplicativo, recomendamos o uso das [extensões de site](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Essas extensões são cópias das [versões oficiais](https://www.python.org) do Python, otimizadas e reempacotadas para o Serviço de Aplicativo do Azure.

Uma extensão de site pode ser implantada por meio do [Portal do Azure](https://portal.azure.com/). Selecione a folha **Ferramentas de Desenvolvimento > Extensões** para seu Serviço de Aplicativo, selecione **Adicionar** e role a lista para encontrar os itens do Python:

![Adicionar a Extensão de Site no portal do Azure](media/template-web-site-extensions.png)

Se você estiver usando modelos de implantação do JSON, será possível especificar a extensão de site como um recurso do site:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Por fim, você pode fazer logon por meio do [console desenvolvimento](https://github.com/projectkudu/kudu/wiki/Kudu-console) e instalar uma extensão de site por ele.

Atualmente, a maneira recomendada de instalar pacotes é usar o console de desenvolvimento após a instalação da extensão de site e execução direta do PIP. É importante usar o caminho completo para o Python ou você poderá executar o caminho incorreto; além disso, geralmente, não é necessário usar um ambiente virtual. Por exemplo:

```command
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Quando implantado em um Serviço de Aplicativo do Azure, o site é executado por atrás do IIS da Microsoft. Para permitir que o site trabalhe com o IIS, é necessário adicionar pelo menos um arquivo `web.config`. Há modelos disponíveis para alguns destinos de implantação comuns disponíveis clicando com o botão direito do mouse no projeto e selecionando **Adicionar > Novo Item...** (consulte a caixa de diálogo abaixo), além disso, essas configurações podem ser facilmente modificadas para outros usos. Consulte a [Referência de configuração do IIS](https://www.iis.net/configreference) para obter informações sobre as definições de configuração disponíveis.

![Modelos de item do Azure](media/template-web-azure-items.png)

Os itens disponíveis incluem:

- Web.config do Azure (FastCGI): adiciona um arquivo `web.config` para quando o aplicativo fornece um objeto [WSGI](https://wsgi.readthedocs.io/en/latest/) para manipular conexões de entrada.
- Web.config do Azure (HttpPlatformHandler): adiciona um arquivo `web.config` para quando o aplicativo escuta um soquete em busca de conexões de entrada.
- Web.config de Arquivos estáticos do Azure: quando você tem um dos arquivos `web.config` acima, adicione o arquivo a um subdiretório para excluí-lo de ser manipulado pelo aplicativo.
- Web.config de depuração remota do Azure: adiciona os arquivos necessários para a depuração remota pelo WebSockets.
- Arquivos de Suporte da Função Web: contém os scripts de implantação padrão para as funções web do serviço de nuvem.
- Arquivos de Suporte da Função de Trabalho: contém os scripts de inicialização e implantação padrão para as funções de trabalho do serviço de nuvem.

Se você adicionar o modelo `web.config` de depuração ao projeto e pretender usar a depuração remota do Python, precisará publicar o site na configuração “Depuração”. Essa configuração é separada da configuração de solução ativa atual e sempre usa como padrão “Versão”. Para alterá-la, abra a guia **Configurações** e use a caixa de combinação **Configuração** no assistente para publicação (consulte a [documentação do Azure](https://azure.microsoft.com/develop/python/) para obter mais informações sobre como criar e implantar em Aplicativos Web do Azure):

![Alterando a configuração de publicação](media/template-web-publish-config.png)

O comando **Converter em Projeto do Serviço de Nuvem do Microsoft Azure** (imagem abaixo) adiciona um projeto do Serviço de Nuvem à solução. Esse projeto inclui as configurações de implantação e a configuração das máquinas virtuais e dos serviços a serem usadas. Use o comando **Publicar** no projeto de nuvem para implantar nos Serviços de Nuvem, o comando **Publicar** no projeto do Python ainda implanta em Sites. Consulte [Projetos do Serviço de Nuvem do Azure](python-azure-cloud-service-project-template.md) para obter mais detalhes.

![Comando Converter em projeto do serviço de nuvem do Microsoft Azure](media/template-web-convert-menu.png)
