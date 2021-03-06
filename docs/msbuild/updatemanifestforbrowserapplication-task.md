---
title: Tarefa UpdateManifestForBrowserApplication | Microsoft Docs
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
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fcc1c9fe8b28b2055c73cad626cc02ef8a56aa98
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="updatemanifestforbrowserapplication-task"></a>Tarefa UpdateManifestForBrowserApplication
A tarefa <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> é executada para adicionar o elemento **\<hostInBrowser />** para o manifesto do aplicativo (*projectname*.exe.manifest) quando um projeto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] é compilado.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ApplicationManifest`|Parâmetro obrigatório **ITaskItem[]**.<br /><br /> Especifica o caminho e o nome do arquivo de manifesto do aplicativo ao qual você deseja adicionar o elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Parâmetro **Booliano** opcional.<br /><br /> Especifica se deseja ou não modificar o manifesto do aplicativo para incluir o elemento **\<hostInBrowser />**. Se for **true**, um novo elemento `<`**hostInBrowser />** será incluído no elemento **\<entryPoint />**. Observe que a inclusão do elemento é cumulativa: se um elemento **\<hostInBrowser />** já existe, ele não é removido nem substituído. Em vez disso, um elemento **\<hostInBrowser />** adicional é criado. Se for **false**, o manifesto do aplicativo não será modificado.|  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] são executados usando a implantação [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] e, portanto, devem ser publicados com os manifestos de implantação e do aplicativo de suporte. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa a [Tarefa GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) para gerar um manifesto do aplicativo.  
  
 Em seguida, para configurar um aplicativo para ser hospedado de um navegador, um elemento adicional, **\<hostInBrowser />**, deve ser adicionado ao manifesto do aplicativo, conforme mostrado no exemplo a seguir:  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 A tarefa <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> é executada quando um projeto [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] é compilado para adicionar o elemento `<hostInBrowser />`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como garantir que o elemento `<hostInBrowser />` seja incluído em um arquivo de manifesto do aplicativo.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Visão geral dos aplicativos de navegador XAML do WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)