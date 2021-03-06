---
title: 'Como: criar um manifesto de produto | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 071bfa46df7e11f760bc32cda0a732388835d2d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-product-manifest"></a>Como criar um manifesto de produto
Para implantar os pré-requisitos para o seu aplicativo, você pode criar um pacote de bootstrapper. Um pacote de bootstrapper contém um arquivo de manifesto de produto único mas um manifesto de pacote para cada localidade. O manifesto de pacote contém aspectos específicos de localização do seu pacote. Isso inclui cadeias de caracteres, os contratos de licença do usuário final e os pacotes de idiomas.  
  
 Para obter mais informações sobre manifestos de produto, consulte [como: criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Criando o manifesto de produto  
  
#### <a name="to-create-the-product-manifest"></a>Para criar o manifesto de produto  
  
1.  Crie um diretório para o pacote de bootstrapper. Este exemplo usa C:\package.  
  
2.  No Visual Studio, crie um novo arquivo XML chamado `product.xml`e salvá-lo para a pasta C:\package.  
  
3.  Adicione o seguinte XML para descrever o código de produto e de namespace XML para o pacote. Substitua o código de produto com um identificador exclusivo para o pacote.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Adicione o XML para especificar que o pacote tem uma dependência. Este exemplo usa uma dependência no Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Adicione XML para listar todos os arquivos que estão no pacote de bootstrapper. Este exemplo usa o nome do arquivo de pacote CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copiar ou mover o arquivo CorePackage.msi para a pasta C:\package.  
  
7.  Adicione XML para instalar o pacote usando comandos de bootstrapper. O inicializador adiciona automaticamente o **/qn** sinalizador para o arquivo. msi, que será instalado silenciosamente. Se o arquivo for um .exe, o inicializador executa o arquivo de .exe usando o shell. O seguinte XML mostra sem argumentos para CorePackage.msi, mas você pode colocar o argumento de linha de comando para o atributo de argumentos.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Adicione o seguinte XML para verificar se este pacote de bootstrapper está instalado. Substitua o código de produto com o GUID para o componente redistribuível.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Adicione XML para alterar o comportamento de bootstrapper dependendo se o componente inicializador já está instalado. Se o componente está instalado, o pacote de bootstrapper não será executado. O XML a seguir verifica se o usuário atual é um administrador, porque esse componente requer privilégios administrativos.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Adicione o XML para definir os códigos de saída se a instalação foi bem-sucedida e se uma reinicialização é necessária. O XML a seguir demonstra que a falha e FailReboot códigos, o que indicam que o bootstrapper não continuará instalando os pacotes de saída.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Adicione o seguinte XML para encerrar a seção de comandos de bootstrapper.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Mova a pasta C:\package para o diretório de bootstrapper do Visual Studio. Para Visual Studio 2010, este é o diretório de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Exemplo  
 O manifesto de produto contém instruções de instalação de pré-requisitos personalizados.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)