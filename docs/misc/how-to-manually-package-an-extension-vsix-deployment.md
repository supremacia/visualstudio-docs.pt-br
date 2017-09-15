---
title: "Como: pacote manualmente uma extens&#227;o (VSIX implanta&#231;&#227;o) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Como: pacote manualmente uma extens&#227;o (VSIX implanta&#231;&#227;o)
Você pode criar um pacote VSIX para encapsular um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão para implantação. Há três maneiras de criar o pacote:  
  
-   Criar um projeto de pacote VSIX usando um dos modelos de extensibilidade que estão incluídos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK. Essa é a opção mais fácil para a maioria dos cenários.  
  
-   Encapsular a saída do seu projeto de extensão em vazio [projeto VSIX](../extensibility/vsix-project-template.md). Recomendamos essa opção para modelos, não há suporte para assemblies e tipos personalizados.  
  
-   Crie manualmente um pacote VSIX. Recomendamos essa opção somente quando as duas opções não estão disponíveis.  
  
 Este documento descreve a terceira opção.  
  
## Criando um pacote VSIX  
 Para empacotar manualmente uma extensão, adicione um arquivo de extension.manifest e um arquivo \[Content\_Types\]. XML no projeto de extensão, colocá\-los em um arquivo compactado junto com a saída de compilação e renomeie o arquivo compactado para que ele tenha uma extensão de nome de arquivo. VSIX. A extensão para ser empacotado deve ser de um tipo que é compatível com o [esquema VSIX](http://msdn.microsoft.com/pt-br/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Os nomes dos arquivos em pacotes VSIX não devem incluir espaços nem caracteres reservados em identificadores de URI \(Uniform Resource\), como definido em [\[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### Para criar manualmente um pacote VSIX  
  
1.  Crie uma extensão do Visual Studio de um tipo que é compatível com o esquema do VSIX.  
  
2.  Crie um arquivo XML e nomeie\- `extension.vsixmanifest`.  
  
3.  Preencha o arquivo de vsixmanifest de acordo com o esquema do VSIX. Para um manifesto de exemplo, consulte [PackageManifest elemento \(elemento raiz, esquema de VSX\)](http://msdn.microsoft.com/pt-br/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Crie um segundo arquivo XML e nomeie\-o `[Content_Types].xml`.  
  
5.  Preencha o arquivo \[Content\_Types\]. XML como especificado em [A estrutura do Content\_types\] arquivo. XML](../Topic/The%20Structure%20of%20the%20Content_types].xml%20File.md).  
  
6.  Colocar ambos os arquivos XML em um diretório com a extensão a ser implantado.  
  
     No caso de um modelo de projeto ou o modelo de item, coloque o arquivo. zip que contém o modelo na mesma pasta dos arquivos XML. Não coloque os arquivos XML no arquivo. zip.  
  
     Em outros casos, coloque os arquivos XML no mesmo diretório que a saída da compilação.  
  
7.  No Windows Explorer, clique na pasta que contém a extensão de conteúdo e os dois arquivos XML, clique em **Enviar para**, e, em seguida, clique em **pasta compactada \(zipada\)**.  
  
8.  Renomeie o arquivo. zip resultante para *Filename*. VSIX, onde *Filename* é o nome do arquivo redistribuível que instala o pacote.  
  
## Consulte também  
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Elemento PackageManifest \(elemento raiz, esquema VSX\)](http://msdn.microsoft.com/pt-br/f8ae42ba-775a-4d2b-976a-f556e147f187)