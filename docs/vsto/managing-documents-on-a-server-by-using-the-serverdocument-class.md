---
title: Gerenciando documentos em um servidor usando a classe ServerDocument | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2120e7c70abaddd4f51c0214a2c5ae517cf955cc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Gerenciando documentos em um servidor usando a classe ServerDocument
  Você pode usar a classe ServerDocument o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para gerenciar vários aspectos das personalizações no nível do documento, mesmo se o Microsoft Office Word e Microsoft Office Excel não são instalados. Você pode executar as seguintes tarefas:  
  
-   Acessar e modificar dados no cache de dados de um documento ou a pasta de trabalho. Para obter mais informações, consulte [trabalhando com armazenado em cache dados no documento](#CachedData).  
  
-   Gerencie o assembly de personalização associado um documento. Para obter mais informações, consulte [Gerenciando a personalização do documento](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Noções básicas sobre a classe ServerDocument  
 A classe ServerDocument é projetada para ser usado em computadores que não têm o Office instalado. Portanto, você normalmente usa essa classe em aplicativos que não se integram com o Office, como projetos de Console ou projetos do Windows Forms, em vez de projetos do Office. Use o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe no assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 A classe ServerDocument pode ser usada para operar em personalizações no nível do documento que foram criadas usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Para obter mais informações sobre o Visual Studio 2010 Tools for Office Runtime e as extensões do Office para o .NET Framework, consulte [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Se você tiver um aplicativo herdado que usa a classe ServerDocument no Visual Studio Tools para Office system (versão 3.0 Runtime), o Visual Studio Tools para Office system (versão 3.0 Runtime) deve ser instalado em computadores que executam o aplicativo. O Visual Studio 2010 Tools para Office Runtime não é possível executar esses aplicativos.  
  
##  <a name="CachedData"></a>Trabalhando com dados armazenados em cache no documento  
 A classe ServerDocument fornece membros, que você pode usar para trabalhar com o cache de dados em documentos personalizados. Para obter mais informações sobre os dados armazenados em cache, consulte [Caching Data](../vsto/caching-data.md) e [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 A tabela a seguir lista os membros que você pode usar para trabalhar com dados armazenados em cache.  
  
|Tarefa|Membro a ser usado|  
|----------|-------------------|  
|Para determinar se um documento tem um cache de dados.|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Para acessar os dados armazenados em cache em um documento.<br /><br /> Para obter mais informações, consulte [acessar dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md).|A propriedade de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> .|  
  
##  <a name="CustomizationInfo"></a>Gerenciando a personalização do documento  
 Você pode usar os membros da classe ServerDocument para gerenciar o assembly de personalização associado um documento. Por exemplo, você pode remover programaticamente a personalização de um documento para que o documento não é parte de uma personalização.  
  
 A tabela a seguir lista os membros que você pode usar para gerenciar o assembly de personalização.  
  
|Tarefa|Membro a ser usado|  
|----------|-------------------|  
|Para determinar se um documento é parte de uma personalização no nível do documento.|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Para anexar programaticamente uma personalização para um documento em tempo de execução.<br /><br /> Para obter mais informações, consulte [como: anexar extensões de código gerenciado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uma da <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> métodos.|  
|Para remover uma personalização de um documento programaticamente no tempo de execução.<br /><br /> Para obter mais informações, consulte [como: remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|O método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Para obter a URL do manifesto de implantação que está associado com o documento.|A propriedade de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> .|  
  
## <a name="see-also"></a>Consulte também  
 [Como: anexar extensões de código gerenciado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Como: remover extensões de código gerenciado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Armazenando dados em cache](../vsto/caching-data.md)  
  