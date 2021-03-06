---
title: 'Como: migrar projetos de extensibilidade para o Visual Studio de 2017 | Microsoft Docs'
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d49ff89f38b0279c60f49ee7d5856d21fd5fc4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Como: migrar projetos de extensibilidade para o Visual Studio de 2017

Este documento explica como atualizar projetos de extensibilidade para 2017 do Visual Studio. Além de descrever como atualizar os arquivos de projeto, ele também descreve como atualizar da versão do manifesto de extensão 2 (v2 VSIX) para o formato manifesto do VSIX do novo versão 3 (v3 VSIX).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalar o Visual Studio de 2017 com cargas de trabalho necessárias

Certifique-se de que sua instalação inclui as seguintes cargas de trabalho:

* Desenvolvimento de área de trabalho do .NET
* Desenvolvimento de extensões do Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abra a solução do VSIX no Visual Studio de 2017

Todos os projetos do VSIX exigirá uma atualização de versão principal unidirecional para 2017 do Visual Studio.

O arquivo de projeto (por exemplo, *. csproj) será atualizado:

* MinimumVisualStudioVersion - agora é definido como 15.0
* OldToolsVersion (se existir anteriormente)-agora é definido como 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Atualizar o pacote do Microsoft.VSSDK.BuildTools NuGet

>**Observação:** se sua solução não fazem referência ao pacote do Microsoft.VSSDK.BuildTools NuGet, você pode ignorar esta etapa.

Para criar sua extensão no v3 VSIX novo formato (versão 3), sua solução precisa ser compilado com as novas ferramentas de compilação VSSDK. Isso será instalado com o Visual Studio de 2017, mas sua extensão do VSIX v2 pode manter uma referência para uma versão anterior por meio do NuGet. Nesse caso, você precisará instalar manualmente uma atualização do pacote do Microsoft.VSSDK.BuildTools NuGet para sua solução.

Para atualizar as referências de NuGet para Microsoft.VSSDK.BuildTools:

* Com o botão direito na solução e escolha **gerenciar pacotes NuGet para solução...**
* Navegue até o **atualizações** guia.
* Selecione Microsoft.VSSDK.BuildTools (versão mais recente).
* Pressione **atualização**.

![Ferramentas de compilação VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Faça as alterações para o manifesto de extensão do VSIX

Para garantir que a instalação do usuário do Visual Studio tem todos os assemblies necessários para executar a extensão, especifique todos os pacotes ou componentes de pré-requisito no arquivo de manifesto de extensão. Quando um usuário tenta instalar a extensão, o VSIXInstaller irá verificar para ver se todos os pré-requisitos estão instalados. Se alguns estiverem ausentes, o usuário será solicitado a instalar os componentes ausentes como parte do processo de instalação de extensão.

>**Observação:** no mínimo, todas as extensões devem especificar o componente de editor de núcleo do Visual Studio como um pré-requisito.

* Edite o arquivo de manifesto de extensão (geralmente chamado de source.extension.vsixmanifest).
* Certifique-se de `InstallationTarget` inclui 15.0.
* Adicione os pré-requisitos de instalação necessários (conforme mostrado no exemplo abaixo).
  * Recomendamos que você especificar apenas as IDs de componente para os pré-requisitos de instalação.
  * Consulte a seção no final deste documento para [instruções sobre como identificar as IDs de componente](#finding-component-ids).

Exemplo:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opção: Usar o designer para fazer alterações para o manifesto de extensão do VSIX

Em vez de editar diretamente o XML do manifesto, você pode usar o novo **pré-requisitos** guia no Designer de manifesto para selecionar os pré-requisitos e o XML será atualizado para você.

>**Observação:** o Designer de manifesto só permitirá que você selecione os componentes (não cargas de trabalho ou pacotes) que estão instalados na instância atual do Visual Studio. Se você precisar adicionar um pré-requisito para uma carga de trabalho, um pacote ou um componente que não está instalado, edite o manifesto XML diretamente.

* Abra o arquivo source.extension.vsixmanifest [Design].
* Selecione **pré-requisitos** guia e pressione **novo** botão.

  ![Designer de manifesto do VSIX](media/vsix-manifest-designer.png)

* O **adicionar novo pré-requisito** janela será aberta.

  ![Adicionar vsix pré-requisito](media/add-vsix-prerequisite.png)

* Clique no menu suspenso **nome** e selecione o pré-requisito desejado.
* Atualize a versão, se necessário.

  >Observação: O campo versão será preenchido previamente com a versão do componente instalado no momento, com um intervalo até a abrangência de chave (mas não incluindo) a próxima versão principal do componente.

  ![Adicionar roslyn pré-requisito](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>Atualizar configurações de depuração de projeto

Se você deseja depurar sua extensão em uma instância experimental do Visual Studio, verifique se as configurações de projeto para **depurar** > **iniciar ação** tem o **iniciar externo programa:** valor definido para o arquivo devenv.exe da instalação do Visual Studio de 2017.

Ele pode parecer com:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Iniciar programa externo](media/start-external-program.png)

>**Observação:** depurar iniciar ação normalmente é armazenada no. arquivo csproj.user. Esse arquivo geralmente está incluído no arquivo. gitignore e, portanto, não será normalmente salvo com outros arquivos de projeto quando o compromisso de controle de origem. Dessa forma, se você tiver extraída sua solução atualizada do controle de origem é provável que o projeto não terá nenhum valor definido para iniciar ação. Novos projetos VSIX criados com o Visual Studio de 2017 terá um. csproj.user arquivo criado com padrões apontando para o diretório de instalação atual do Visual Studio. No entanto se você estiver migrando uma extensão do VSIX v2, é provável que o. arquivo csproj.user contém referências ao diretório de instalação da versão do Visual Studio anteriores. Definir o valor de **depurar** > **iniciar ação** permitirá que a instância experimental do Visual Studio correta iniciar quando você tentar depurar sua extensão.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verifique se a extensão de compilação está corretamente (como um v3 VSIX)

* Compile o projeto do VSIX.
* Descompacte o VSIX gerado.
  * Por padrão, a vida do arquivo VSIX dentro bin/Debug ou bin/Release como .vsix [YourCustomExtension].
  * Renomeie .vsix para. zip para exibir facilmente o conteúdo.
* Verificar a existência dos três arquivos:
  * Extension.vsixmanifest
  * manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Verificar quando todos os pré-requisitos necessários estão instalados

Verifique se o VSIX é instalado com êxito em um computador com os pré-requisitos necessários instalados.

>**Observação:** antes de instalar qualquer extensão, por favor, feche todas as instâncias do Visual Studio.

Tentativa de instalar a extensão:

* No Visual Studio de 2017

![Instalador do VSIX no Visual Studio de 2017](media/vsixinstaller-vs-2017.png)

* Opcional: Verificação em versões anteriores do Visual Studio.
  * Prova de compatibilidade com versões anteriores.
  * Deve funcionar para Visual Studio 2012, o Visual Studio 2013, o Visual Studio 2015.
* Opcional: Verifique se o verificador de versão do instalador VSIX oferece uma opção de versões.
  * Inclui as versões anteriores do Visual Studio (se instalado).
  * Inclui 2017 do Visual Studio.

Se o Visual Studio foi aberto recentemente, você verá uma caixa de diálogo como esta:

![VS processos em execução](media/vs-running-processes.png)

Aguarde até que os processos desligar ou terminar manualmente as tarefas. Você pode encontrar os processos pelo nome listado, ou com o PID listados entre parênteses.

>**Observação:** esses processos não seja automaticamente desligado enquanto uma instância do Visual Studio está em execução. Verifique se você encerrou todas as instâncias do Visual Studio no computador - incluindo aqueles de outros usuários, e continuará a tentar novamente.

## <a name="check-when-missing-the-required-prerequisites"></a>Verificar quando tem os pré-requisitos necessários

* Tentativa de instalar a extensão em um computador com Visual Studio 2017 que não CONTÊM todos os componentes definidos nos pré-requisitos (acima).
* Verifique se a instalação identifica o componente ausente/s e lista como um pré-requisito no VSIXInstaller.
* Observação: Elevação será necessária se todos os pré-requisitos devem ser instalados com a extensão.

![pré-requisito ausente vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Decidir sobre componentes

Ao procurar por suas dependências, você descobrirá que uma dependência foi possível mapear para vários componentes. Para determinar quais dependências, você deve especificar como o pré-requisito, sugerimos que você escolha um componente que tem uma funcionalidade semelhante a sua extensão e considerar também os usuários e que tipo de componentes seria provavelmente instalaram ou não se a instalação. Também recomendamos criando suas extensões de uma maneira em que os pré-requisitos necessários atendem apenas o mínimo que permitirá que a extensão a ser executada, bem como para recursos adicionais quer que elas fiquem inativos se determinados componentes não são detectados.

Para fornecer mais orientações, identificamos alguns tipos comuns de extensão e seus pré-requisitos sugeridos:

Tipo de extensão | Nome de Exibição | Id
--- | --- | ---
Editor | Editor do Visual Studio Core  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo da carga de trabalho de área de trabalho gerenciada | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Depurador | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Localizar IDs de componente

A lista de componentes, classificados por produto do Visual Studio está em [IDs de componente e de carga de trabalho do Visual Studio 2017](https://aka.ms/vs2017componentIDs). Use essas IDs de componente para suas IDs de pré-requisito em seu manifesto.

Se você não souber qual componente contém um download de binários, específico do [componente -> planilha mapeamento binário](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Há quatro colunas na planilha do Excel: **nome do componente**, **ComponentId**, **versão**, e **binário / nomes de arquivo**.  Você pode usar os filtros para pesquisar e localizar os binários e componentes específicos.

Para todas as suas referências, determine quais são no componente core editor (Microsoft.VisualStudio.Component.CoreEditor).  No mínimo, é necessário o componente de editor principal a ser especificado como um pré-requisito para todas as extensões. Das referências restantes que não estão no editor de núcleo, adicionar filtros a **binários / nomes de arquivos** seção para encontrar os componentes que têm algum subconjunto essas referências.

Exemplos:

* Se você tiver uma extensão de depurador e sabe que seu projeto tem uma referência a VSDebugEng.dll e VSDebug.dll, clique no botão de filtro no **binários / nomes de arquivos** cabeçalho.  Procurar por "VSDebugEng.dll" e selecione Okey.  Em seguida, clique no botão de filtro de **binários / nomes de arquivos** cabeçalho novamente e procure "VSDebug.dll".  Marque a caixa de seleção "Adicionar seleção atual ao filtro" e selecione Okey.  Agora examine a **nome do componente** para localizar um componente mais relacionadas ao seu tipo de extensão. Neste exemplo, você pode escolher Just-In-Time do depurador e adicioná-lo ao seu vsixmanifest.
* Se você souber que seu projeto lida com elementos de depurador, você pode pesquisar em "depurador" na caixa de filtro de pesquisa para ver quais componentes contêm depurador em seu nome.

## <a name="specifying-a-visual-studio-2017-release"></a>Especificando uma versão do Visual Studio de 2017

Se sua extensão requer uma versão específica do Visual Studio de 2017, por exemplo, depende de um recurso lançado no 15,3, você deve especificar o número de compilação em seu VSIX **InstallationTarget**. Por exemplo, a versão 15,3 tem um número de compilação de '15.0.26730.3'. Você pode ver o mapeamento de versões para criar números [aqui](../install/visual-studio-build-numbers-and-release-dates.md). Usando o número de versão '15,3' não funcionará corretamente.

Se sua extensão requer 15,3 ou superior, você deve declarar o **InstallationTarget versão** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```