---
title: "Referência da Tarefa do WPF MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5dbb779e7f9d12465aab5abf4051677948cb6d14
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="wpf-msbuild-task-reference"></a>Referência das tarefas do WPF MSBuild
O processo de build do Windows Presentation Foundation (WPF) estende o Microsoft Build Engine (MSBuild) com um conjunto adicional de tarefas de build, incluindo tarefas para compilar recursos de marcação e o processo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifica um conjunto de recursos de origem que será inserido em um assembly. Se um recurso não for localizável, ele será inserido no assembly principal do aplicativo; caso contrário, ele será inserido em um assembly satélite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Gera um assembly se pelo menos uma página [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] em um projeto referencia um tipo declarado localmente no projeto. O assembly gerado será removido após concluir o processo de build ou se o processo de build falhar.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Retorna o diretório do tempo de execução [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] atual.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Converte arquivos de projeto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] não localizáveis para o formato binário compilado.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Executa a compilação de marcação de segunda passagem em [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] arquivos que fazem referência a tipos no mesmo projeto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Mescla os atributos de localização e comentários de um ou mais [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos de formato binário em um único arquivo para todo o assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Insere um ou mais recursos (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em formato binário e outros tipos de extensão) em um arquivo .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Verifica, atualiza ou remove identificadores exclusivos (UIDs), para localizar todos os [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] elementos que são incluídos na fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Adiciona o elemento **\<hostInBrowser / >** para o manifesto do aplicativo (*projectname*.exe.manifest) quando um [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] projeto é compilado.  
  
## <a name="see-also"></a>Consulte também  
 [MSBuild](../msbuild/msbuild.md)