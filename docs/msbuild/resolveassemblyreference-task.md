---
title: Tarefa ResolveAssemblyReference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveAssemblyReference
- MSBuild.ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects
- MSBuild.ResolveAssemblyReference.FoundConflict
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveAssemblyReference task [MSBuild]
- MSBuild, ResolveAssemblyReference task
ms.assetid: 4d56d848-b29b-4dff-86a2-0a96c9e4a170
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: cf23ae07cbe6fda773405ca4a308487e0c92fec0
ms.contentlocale: pt-br
ms.lasthandoff: 06/03/2017

---
# <a name="resolveassemblyreference-task"></a>Tarefa ResolveAssemblyReference
Determina todos os assemblies que dependem dos assemblies especificados. Isso inclui as segundas e `n`enésimas dependências.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveAssemblyReference`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AllowedAssemblyExtensions`|Parâmetro `String[]` opcional.<br /><br /> As extensões de nome de arquivo do assembly que serão usadas ao resolver referências. As extensões de nome de arquivo padrão são .exe e .dll.|  
|`AllowedRelatedFileExtensions`|Parâmetro `String[]` opcional.<br /><br /> As extensões de nome de arquivo que serão usadas para uma pesquisa de arquivos que estão relacionados uns aos outros. As extensões padrão são .pdb e .xml.|  
|`AppConfigFile`|Parâmetro `String` opcional.<br /><br /> Especifica um arquivo app.config do qual serão analisados e extraídos os mapeamentos bindingRedirect. Se esse parâmetro for especificado, o parâmetro `AutoUnify` deverá ser `false`.|  
|`AutoUnify`|Parâmetro `Boolean` opcional.<br /><br /> Esse parâmetro é usado para criar assemblies, como DLLs, que não podem ter um arquivo App.Config normal.<br /><br /> Quando `true`, o gráfico de dependência resultante é tratado automaticamente como se um arquivo App.Config tivesse passado para o parâmetro AppConfigFile. Esse arquivo App.Config virtual tem uma entrada de bindingRedirect para cada conjunto conflitante de assemblies, de modo que o assembly de versão mais alto é escolhido. Uma consequência disso é que nunca haverá um aviso sobre assemblies conflitantes porque cada conflito terá sido resolvido.<br /><br /> Quando `true`, cada remapeamento distinto resultará em um comentário de alta prioridade, mostrando as versões nova e antiga e que `AutoUnify` foi `true`.<br /><br /> Quando `true`, o parâmetro AppConfigFile deverá estar vazio<br /><br /> Quando `false`, nenhum remapeamento da versão do assembly ocorrerá automaticamente. Quando existir duas versões de um assembly, um aviso será emitido.<br /><br /> Quando `false`, cada conflito distinto entre versões diferentes do mesmo assembly resultará em um comentário de alta prioridade. Esses comentários são seguidos por um único aviso. O aviso tem um código de erro exclusivo e contém o texto "Encontrados conflitos entre diferentes versões de referência e assemblies dependentes".|  
|`Assemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os itens para os quais as dependências e caminhos completos devem ser identificados. Esses itens podem ter nomes simples como "Sistema" ou nomes fortes, como "System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089."<br /><br /> Itens passados para esse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `Private`: `Boolean`. Se `true`, então o item será copiado localmente. O valor padrão é `true`.<br />Valor -   `HintPath`: `String`. Especifica o caminho e nome de arquivo que será usado como referência. Isso é usado quando {HintPathFromItem} é especificado no parâmetro `SearchPaths`. O valor padrão é uma cadeia de caracteres vazia.<br />Valor -   `SpecificVersion`: `Boolean`. Se `true`, então o nome exato especificado no atributo `Include` deverá corresponder. Se `false`, qualquer assembly com o mesmo nome simples funcionará. Se `SpecificVersion` não for especificado, então a tarefa examinará o valor do atributo `Include` do item. Se o atributo for um nome simples, ele se comportará como se `SpecificVersion` tivesse sido `false`. Se o atributo for um nome forte, ele se comportará como se `SpecificVersion` tivesse sido `true`.<br />     Quando usado com um tipo de item de referência, o atributo `Include` deve ser o nome completo de fusão do assembly a ser resolvido. O assembly será resolvido apenas se a fusão corresponder exatamente ao atributo `Include`.<br />     Quando um projeto tem como alvo uma versão do .NET Framework e referencia um assembly compilado para uma versão posterior do .NET Framework, a referência será resolvida apenas se ela tiver `SpecificVersion` definido como `true`.<br />     Quando um projeto tem como alvo um perfil e faz referencia um assembly que não está no perfil, a referência será resolvida apenas se ela tiver `SpecificVersion` definido como `true`.<br />Valor -   `ExecutableExtension`: `String`. Quando presente, o assembly resolvido deve ter essa extensão. Quando ausente, o .dll é considerado primeiro, seguido por .exe, para cada diretório examinado.<br />Valor -   `SubType`: `String`. Somente os itens com metadados SubType vazios serão resolvidos em caminhos de assembly completo. Itens com metadados SubType não vazios são ignorados.<br />Valor -   `AssemblyFolderKey`: `String`. Esses metadados têm suporte para fins de herdado. Ele especifica uma chave do Registro definida pelo usuário, como "hklm\\*VendorFolder*", que `Assemblies` deve usar para resolver referências de assembly.|  
|`AssemblyFiles`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica uma lista de assemblies totalmente qualificados para encontrar as dependências.<br /><br /> Itens passados para esse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br /> -   `Private`: um valor `Boolean` opcional. Se for verdadeiro, então o item será copiado localmente.<br />-   `FusionName`: metadados `String` opcionais. Especifica o nome simples ou forte para esse item. Se esse atributo estiver presente, isso poderá economizar tempo porque o arquivo do assembly não precisa ser aberto para obter o nome.|  
|`AutoUnify`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o gráfico de dependência resultante será tratado automaticamente como se um arquivo App.Config tivesse passado para o parâmetro AppConfigFile. Esse arquivo App.Config virtual tem uma entrada de bindingRedirect para cada conjunto conflitante de assemblies, de modo que o assembly de versão mais recente é escolhido. Um resultado disso é que nunca haverá um aviso sobre assemblies conflitantes porque cada conflito terá sido resolvido. Cada remapeamento distintos causará um comentário de alta prioridade que indica as versões antigas e novas e o fato de que isso foi feito automaticamente porque `AutoUnify` foi `true`.<br /><br /> Se `false`, nenhum remapeamento da versão do assembly ocorrerá automaticamente. Quando existir duas versões de um assembly, um aviso será emitido. Cada conflito distinto entre versões diferentes do mesmo assembly resultará em um comentário de alta prioridade. Depois que todos esses comentários forem exibidos, haverá um único aviso com um único código de erro e texto informando que foram "encontrados conflitos entre diferentes versões de referência e assemblies dependentes".<br /><br /> O valor padrão é `false`.|  
|`CandidateAssemblyFiles`|Parâmetro `String[]` opcional.<br /><br /> Especifica uma lista de assemblies que serão usados para o processo de pesquisa e resolução. Os valores passados para este parâmetro devem ser nomes de arquivos absolutos ou nomes de arquivos relacionados ao projeto.<br /><br /> Os assemblies nesta lista serão considerados quando o parâmetro `SearchPaths` contiver {CandidateAssemblyFiles} como um dos caminhos a serem considerados.|  
|`CopyLocalDependenciesWhenParentReferenceInGac`|Parâmetro <xref:System.Boolean> opcional.<br /><br /> Se for verdadeiro, para determinar se uma dependência deverá ser copiada localmente, uma das verificações feitas é ver se a referência pai no arquivo de projeto tem metadados particulares definidos. Se definido, o valor particular será usado como uma dependência.<br /><br /> Se os metadados não estiverem definidos, então a dependência passará pelas mesmas verificações da referência pai. Uma dessas verificações é ver se a referência está no GAC. Se uma referência estiver no GAC, então ela não será copiada localmente, porque ela é considerada como estando no GAC no computador de destino. Isso é aplicável somente a uma referência específica e não a suas dependências.<br /><br /> Por exemplo, uma referência no arquivo de projeto que está no GAC não é copiada localmente, mas suas dependências são copiadas localmente porque elas não estão no GAC.<br /><br /> Se falso, as referências de arquivo de projeto são verificadas para ver se elas estão no GAC e são copiadas localmente, conforme apropriado.<br /><br /> As dependências são verificadas para ver se elas estão no GAC e também são verificadas para ver se a referência pai do arquivo de projeto está no GAC.<br /><br /> Se a referência pai do arquivo de projeto estiver no GAC, a dependência não será copiada localmente.<br /><br /> Independentemente de esse parâmetro ser verdadeiro ou falso, se houver várias referências pai e uma delas não estiver no GAC, todas elas serão copiadas localmente.|  
|`CopyLocalFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Retorna todos os arquivos nos parâmetros `ResolvedFiles`, `ResolvedDependencyFiles`, `RelatedFiles`, `SatelliteFiles` e `ScatterFiles` e que têm os metadados de item `CopyLocal` com um valor de `true`.|  
|`FilesWritten`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens gravados em disco.|  
|`FindDependencies`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, as dependências serão encontradas. Caso contrário, apenas as referências principais serão encontradas. O valor padrão é `true`.|  
|`FindRelatedFiles`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, arquivos relacionados, como arquivos .pdb e arquivos .xml serão encontrados. O valor padrão é `true`.|  
|`FindSatellites`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os assemblies satélites serão encontrados. O valor padrão é `true.`|  
|`FindSerializationAssemblies`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa pesquisará os assemblies de serialização. O valor padrão é `true`.|  
|`FullFrameworkAssemblyTables`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os itens que têm metadados "FrameworkDirectory" para associar uma lista redist a um diretório de estrutura específica. Se a associação não for feita, um erro será registrado. A lógica de RAR (referência do assembly de resolução) usará o diretório da estrutura de destino se um FrameworkDirectory não estiver definido.|  
|`FullFrameworkFolders`|Parâmetro opcional <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Especifica o conjunto de pastas que contêm um diretório RedistList. Esse diretório representa a estrutura completa para um perfil de cliente, por exemplo, %programfiles%\reference assemblies\microsoft\framework\v4.0.|  
|`FullTargetFrameworkSubsetNames`|Parâmetro `String[]` opcional.<br /><br /> Contém uma lista de nomes de subconjunto de estrutura de destino. Se um nome de subconjunto na lista corresponde a um na propriedade de nome `TargetFrameworkSubset`, o sistema exclui esse subconjunto de estrutura de destino específico no momento do build.|  
|`IgnoreDefaultInstalledAssemblyTables`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, então a tarefa pesquisa e usa as tabelas de assembly instaladas adicionais (ou "Lista Redist") que estão localizadas no diretório \RedistList em `TargetFrameworkDirectories`. O valor padrão é `false.`|  
|`IgnoreDefaultInstalledAssemblySubsetTables`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, então a tarefa pesquisa e usa as tabelas de subconjunto de assembly instaladas adicionais (ou "Listas de Subconjunto") que estão localizadas no diretório \SubsetList em `TargetFrameworkDirectories`. O valor padrão é `false.`|  
|`InstalledAssemblySubsetTables`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Contém uma lista de arquivos XML que especificam os assemblies que devem estar no subconjunto do destino.<br /><br /> Como opção, os itens nessa lista podem especificar os metadados de "FrameworkDirectory" para associar a um `InstalledAssemblySubsetTable`<br /><br /> com um diretório de estrutura específico.<br /><br /> Se houver apenas um elemento `TargetFrameworkDirectories`, então todos os itens na lista que não têm os metadados de "FrameworkDirectory" são tratados como se eles fossem definidos como o valor exclusivo que é passado para `TargetFrameworkDirectories`.|  
|`InstalledAssemblyTables`|Parâmetro `String` opcional.<br /><br /> Contém uma lista de arquivos XML que especificam os assemblies que devem ser instalados no computador de destino.<br /><br /> Quando `InstalledAssemblyTables` estiver definido, as versões anteriores dos assemblies na lista serão mescladas em versões mais recentes listadas no XML. Além disso, os assemblies que têm uma configuração de InGAC = 'true' são considerados pré-requisitos e são definidos como CopyLocal = 'false', a menos que explicitamente substituídos.<br /><br /> Como opção, os itens nessa lista podem especificar os metadados de "FrameworkDirectory" para associar a um `InstalledAssemblyTable` com um diretório de estrutura específico.  No entanto, essa configuração será ignorada a menos que o nome do Redist comece com<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Se houver apenas um elemento `TargetFrameworkDirectories`, então todos os itens na lista que não têm os metadados de "FrameworkDirectory" são tratados como se eles fossem definidos como o valor exclusivo que é passado<br /><br /> para `TargetFrameworkDirectories`.|  
|`LatestTargetFrameworkDirectories`|Parâmetro `String[]` opcional.<br /><br /> Especifica uma lista de diretórios que contêm as listas redist para a estrutura mais recente que possa ser direcionada no computador. Se isso não for definido a estrutura mais recente instalada no computador para um identificador de estrutura de destino fornecido será usada.|  
|`ProfileName`|Parâmetro `String` opcional.<br /><br /> -   Especifica o nome do perfil da estrutura que será direcionado. Por exemplo, cliente, Web ou rede.|  
|`RelatedFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém os arquivos relacionados, como arquivos XML e .pdb que têm o mesmo nome de base como uma referência.<br /><br /> Os arquivos listados nesse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `Primary`: `Boolean`. Se `true`, então o item do arquivo foi passado para a matriz usando o parâmetro `Assemblies`. O valor padrão é `false`.<br />Valor -   `CopyLocal`: `Boolean`. Indica se a referência será copiada no diretório de saída.|  
|`ResolvedDependencyFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém os caminhos de ordem *n* para as dependências. Esse parâmetro não inclui referências de primeira ordem, que estão contidas no parâmetro `ResolvedFiles`.<br /><br /> Os itens nesse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `CopyLocal`: `Boolean`. Indica se a referência será copiada no diretório de saída.<br />Valor -   `FusionName`: `String`. Especifica o nome para essa dependência.<br />Valor -   `ResolvedFrom`: `String`. Especifica o caminho de pesquisa literal do qual este arquivo foi resolvido.|  
|`ResolvedFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém uma lista de todas as referências primárias resolvidas para caminhos completos.<br /><br /> Os itens nesse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `CopyLocal`: `Boolean`. Indica se a referência será copiada no diretório de saída.<br />Valor -   `FusionName`: `String`. Especifica o nome para essa dependência.<br />Valor -   `ResolvedFrom`: `String`. Especifica o caminho de pesquisa literal do qual este arquivo foi resolvido.|  
|`SatelliteFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Especifica todos os arquivos satélites encontrados. Eles serão CopyLocal=true se a referência ou a dependência que causou a existência deste item for CopyLocal=true.<br /><br /> Os itens nesse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `CopyLocal`: `Boolean`. Indica se a referência será copiada no diretório de saída. Esse valor é `true` se a referência ou a dependência que causou a existência deste item tiver um valor `CopyLocal` de `true`.<br />Valor -   `DestinationSubDirectory`: `String`. Especifica o diretório de destino relativo ao qual copiar este item.|  
|`ScatterFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém os arquivos de dispersão associados a um dos assemblies.<br /><br /> Os itens nesse parâmetro podem, opcionalmente, ter os metadados de item a seguir:<br /><br />Valor  -   `CopyLocal`: `Boolean`. Indica se a referência será copiada no diretório de saída.|  
|`SearchPaths`|Parâmetro `String[]` obrigatório.<br /><br /> Especifica os diretórios ou locais especiais que são pesquisados para localizar os arquivos no disco que representam os assemblies. A ordem na qual os caminhos de pesquisa são listados é importante. Para cada assembly, a lista de caminhos é pesquisada da esquerda para a direita. Quando um arquivo que representa o assembly for encontrado, a pesquisa será interrompida e a pesquisa do próximo assembly começará.<br /><br /> Esse parâmetro aceita uma lista delimitada por ponto-e-vírgula dos valores que podem ser caminhos de diretório ou valores literais especiais da lista abaixo:<br /><br /> -   `{HintPathFromItem}`: especifica que a tarefa examinará os metadados `HintPath` do item de base.<br />-   `{CandidateAssemblyFiles}`: especifica que a tarefa examinará os arquivos transmitidos por meio do parâmetro `CandidateAssemblyFiles`.<br />-   `{Registry:_AssemblyFoldersBase_, _RuntimeVersion_, _AssemblyFoldersSuffix_}`: especifica que a tarefa pesquisará em pastas adicionais especificadas no Registro. `_AssemblyFoldersBase_`, `_RuntimeVersion_` e `_AssemblyFoldersSuffix_` devem ser substituídos por valores específicos para o local do Registro a ser pesquisado. A especificação do padrão nos destinos comuns é `{Registry:$(FrameworkRegistryBase),$(TargetFrameworkVersion),$(AssemblyFoldersSuffix)$(AssemblyFoldersExConditions)}`.<br />-   `{AssemblyFolders}`: especifica que a tarefa usará o esquema de localizar assemblies de Registro do Visual Studio.NET 2003.<br />-   `{GAC}`: especifica a tarefa que pesquisará no GAC (Cache de Assembly Global).<br />-   `{RawFileName}`: especifica que a tarefa considerará o valor `Include` do item como um nome de arquivo e caminho exato.|  
|`SerializationAssemblyFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém os assemblies de serialização XML encontrados. Esses itens serão marcados como CopyLocal=true se a referência ou a dependência que causou a existência deste item for CopyLocal=true.<br /><br /> O CopyLocal dos metadados `Boolean` indica se a referência fornecida deve ser copiada para o diretório de saída.|  
|`Silent`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, nenhuma mensagem será registrada. O valor padrão é `false`.|  
|`StateFile`|Parâmetro `String` opcional.<br /><br /> Especifica um nome de arquivo que indica onde salvar o estado de build intermediária para essa tarefa.|  
|`SuggestedRedirects`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` de saída opcional somente leitura.<br /><br /> Contém um item para cada identidade de assembly distinto em conflito, independentemente do valor do parâmetro `AutoUnify`. Isso inclui cada cultura e PKT encontrados que não tinham uma entrada bindingRedirect adequada no arquivo de configuração de aplicativo.<br /><br /> Cada item contém, opcionalmente, as informações a seguir:<br /><br />Atributo  -   `Include`: contém o nome completo da família do assembly com um valor de campo de versão de 0.0.0.0<br />Metadados de item -   `MaxVersion`: contém o número máximo de versão.|  
|`TargetedRuntimeVersion`|Parâmetro `String` opcional.<br /><br /> Especifica a versão de tempo de execução para o destino, por exemplo, 2.0.57027 ou v2.0.57027.|  
|`TargetFrameworkDirectories`|Parâmetro `String[]` opcional.<br /><br /> Especifica o caminho do diretório da estrutura de destino. Este parâmetro é necessário para determinar o status de CopyLocal para os itens resultantes.<br /><br /> Se esse parâmetro não for especificado, nenhum item resultante terá um valor CopyLocal de `true` a menos que tenham explicitamente um valor de metadados `Private` de `true` em seu item de origem.|  
|`TargetFrameworkMoniker`|Parâmetro `String` opcional.<br /><br /> O TargetFrameworkMoniker para monitorar, se houver. Isso é usado para registro em log.|  
|`TargetFrameworkMonikerDisplayName`|Parâmetro `String` opcional.<br /><br /> O nome de exibição do TargetFrameworkMoniker para monitorar, se houver. Isso é usado para registro em log.|  
|`TargetFrameworkSubsets`|Parâmetro `String[]` opcional.<br /><br /> Contém uma lista de nomes de subconjunto da estrutura de destino que será pesquisada em diretórios da estrutura de destino.|  
|`TargetFrameworkVersion`|Parâmetro `String` opcional.<br /><br /> A versão da estrutura de destino do projeto. O valor padrão é vazio, o que significa que não há nenhuma filtragem para as referências com base na estrutura de destino.|  
|`TargetProcessorArchitecture`|Parâmetro `String` opcional.<br /><br /> A arquitetura do processador de destino preferencial. Usada para resolver referências de GAC (Cache de Assembly Global).<br /><br /> Esse parâmetro pode ter um valor de `x86`, `IA64` ou `AMD64`.<br /><br /> Se esse parâmetro estiver ausente, a tarefa considerará primeiro assemblies que correspondem à arquitetura do processo em execução no momento. Se nenhum assembly for encontrado, a tarefa considerará os assemblies no GAC com valor `ProcessorArchitecture` de `MSIL` ou nenhum valor `ProcessorArchitecture`.|  
  
## <a name="warnings"></a>Avisos  
 Os seguintes avisos são registrados:  
  
-   `ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects`  
  
-   `ResolveAssemblyReference.SuggestedRedirects`  
  
-   `ResolveAssemblyReference.FoundConflicts`  
  
-   `ResolveAssemblyReference.AssemblyFoldersExSearchLocations`  
  
-   `ResolveAssemblyReference.UnifiedPrimaryReference`  
  
-   `ResolveAssemblyReference.PrimaryReference`  
  
-   `ResolveAssemblyReference.UnifiedDependency`  
  
-   `ResolveAssemblyReference.UnificationByAutoUnify`  
  
-   `ResolveAssemblyReference.UnificationByAppConfig`  
  
-   `ResolveAssemblyReference.UnificationByFrameworkRetarget`  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
