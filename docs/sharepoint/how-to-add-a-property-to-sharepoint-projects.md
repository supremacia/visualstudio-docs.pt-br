---
title: 'Como: adicionar uma propriedade a projetos do SharePoint | Microsoft Docs'
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4318550e74d5324195de173659d96abaf952979
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Como adicionar uma propriedade a projetos do SharePoint
  Você pode usar uma extensão de projeto para adicionar uma propriedade a qualquer projeto do SharePoint. A propriedade aparece no **propriedades** janela quando o projeto for selecionado no **Gerenciador de soluções**.  
  
 As etapas a seguir pressupõem que você já tenha criado uma extensão de projeto. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>Para adicionar uma propriedade a um projeto do SharePoint  
  
1.  Defina uma classe com uma propriedade pública que representa a propriedade que você está adicionando a projetos do SharePoint. Se você quiser adicionar várias propriedades, você pode definir todas as propriedades na mesma classe ou em classes diferentes.  
  
2.  No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementação, o identificador de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos do *projectService* parâmetro.  
  
3.  No manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, adicionar uma instância de sua classe de propriedades para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> coleção de parâmetro dos argumentos do evento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar duas propriedades a projetos do SharePoint. Uma propriedade persiste os dados no arquivo de opção de usuário do projeto (o. arquivo csproj.user ou. vbproj.user arquivo). Outra propriedade mantém seus dados no arquivo de projeto (arquivo. csproj ou. vbproj).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Noções básicas sobre o código  
 Para garantir que a mesma instância do `CustomProjectProperties` classe é usada sempre que o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento ocorre, o exemplo de código adiciona o objeto de propriedades para o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do tempo de projeto primeiro esse evento ocorre. O código recupera esse objeto sempre que esse evento ocorre novamente. Para obter mais informações sobre como usar o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade para associar dados de projetos, consulte [associando dados personalizados com extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para manter as alterações aos valores de propriedade, o **definir** acessadores para as propriedades de usam as seguintes APIs:  
  
-   `CustomUserFileProperty`usa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriedade para salvar seu valor para o arquivo de opção de usuário do projeto.  
  
-   `CustomProjectFileProperty`usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método para salvar seu valor para o arquivo de projeto.  
  
 Para obter mais informações sobre como manter dados nesses arquivos, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especificar o comportamento de propriedades personalizadas  
 Você pode definir como uma propriedade personalizada é exibida e o comportamento de **propriedades** janela aplicando atributos do <xref:System.ComponentModel> namespace para a definição da propriedade. Os seguintes atributos são úteis em vários cenários:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica o nome da propriedade que aparece no **propriedades** janela.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica a cadeia de caracteres de descrição que aparece na parte inferior da **propriedades** janela quando a propriedade é selecionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica o valor padrão da propriedade.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica uma conversão personalizada entre a cadeia de caracteres que é exibida no **propriedades** janela e um valor de propriedade de cadeia de caracteres não.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica um editor personalizado para usar para modificar a propriedade.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo projetos SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Como: adicionar um Item de Menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  