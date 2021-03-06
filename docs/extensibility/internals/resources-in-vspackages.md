---
title: Recursos em VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee9d108e7a7a6a5bd971b20c12858edf28ac0cf3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="resources-in-vspackages"></a>Recursos em VSPackages
Você pode inserir recursos localizados em nativo da interface do usuário DLLs satélite, DLLs satélite gerenciado, ou em um VSPackage gerenciado em si.  
  
 Alguns recursos não podem ser inseridos no VSPackages. Os seguintes tipos gerenciados podem ser inseridos:  
  
-   Cadeias de caracteres  
  
-   Chaves de carregamento (que também são cadeias de caracteres)  
  
-   Ícones da janela de ferramenta  
  
-   Arquivos de saída de tabela de comando (CTO) compilados  
  
-   Bitmaps CTO  
  
-   Ajuda de linha de comando  
  
-   Sobre dados de caixa de diálogo  
  
 Recursos em um pacote gerenciado são selecionados por ID de recurso. Uma exceção é o arquivo CTO, que deve ser nomeado CTMENU. O arquivo CTO deve aparecer na tabela de recursos, como um `byte[]`. Todos os outros itens de recurso são identificados por tipo.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atributo para indicar ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se recursos gerenciados estão disponíveis.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Configuração <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> dessa maneira indica que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devem ignorar DLLs satélite de não gerenciado quando ele procura por recursos, por exemplo, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] encontra dois ou mais recursos que têm a mesma ID de recurso, ele usa o primeiro recurso encontra.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir é uma representação gerenciada de um ícone de janela de ferramenta.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 O exemplo a seguir demonstra como incorporar a matriz de bytes CTO, que deve ser nomeada CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Notas de implementação  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]carregamento de atrasos de VSPackages sempre que possível. Uma consequência de incorporação de um arquivo CTO em um VSPackage é que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve carregar todos os tais VSPackages na memória durante a instalação, quando ele cria uma tabela de comandos mesclada. Recursos podem ser extraídos de um VSPackage examinando os metadados sem executar código no VSPackage. O VSPackage não foi inicializado neste momento, portanto, a perda de desempenho é mínimo.  
  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] solicitações de um recurso de um VSPackage após a instalação, esse pacote é provável que já seja carregado e inicializado, portanto, a perda de desempenho é mínimo.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando VSPackages](../../extensibility/managing-vspackages.md)   
 [Recursos localizados em aplicativos MFC: DLLs satélites](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
