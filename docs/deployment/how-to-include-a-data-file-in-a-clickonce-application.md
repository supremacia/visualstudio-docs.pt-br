---
title: 'Como: incluir um arquivo de dados em um aplicativo ClickOnce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a7ddfdb0518a8e3154d966fdea884bf7f2e3ea37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Como incluir um arquivo de dados em um aplicativo ClickOnce
Cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo instalar é atribuído a um diretório de dados no disco local do computador de destino, onde o aplicativo pode gerenciar seus próprios dados. Arquivos de dados podem incluir arquivos de qualquer tipo: arquivos de texto, arquivos XML ou até mesmo arquivos de banco de dados (. mdb) do Microsoft Access. Os procedimentos a seguir mostram como adicionar um arquivo de dados de qualquer tipo em seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Para incluir um arquivo de dados usando Mage.exe  
  
1.  Adicione o arquivo de dados para o diretório de aplicativo com o restante dos arquivos do aplicativo.  
  
     Normalmente, o diretório de seu aplicativo será um diretório rotulado com a versão atual da implantação — por exemplo, v 1.0.0.0.  
  
2.  Atualize o manifesto do aplicativo para o arquivo de dados da lista.  
  
     **v 1.0.0.0 do imagem -u v1.0.0.0\Application.manifest - FromDirectory**  
  
     Para executar essa tarefa cria novamente a lista de arquivos em seu manifesto de aplicativo e também gera automaticamente as assinaturas de hash.  
  
3.  Abra o manifesto do aplicativo em seu preferencial de texto ou editor XML e localize o `file` elemento para o arquivo adicionado recentemente.  
  
     Se você adicionou um arquivo XML denominado `Data.xml`, o arquivo será semelhante ao exemplo de código a seguir.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Adicione o atributo `type` para esse elemento e fornecê-lo com um valor de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Assinar novamente o manifesto do aplicativo usando o par de chaves ou certificado e assinar novamente o manifesto de implantação.  
  
     Você deve assinar novamente o manifesto de implantação porque o hash do manifesto do aplicativo foi alterado.  
  
     **-cf cert_file - pwd senha de manifesto do aplicativo de -s de imagem**  
  
     **manifesto do aplicativo manifesto - appm -u implantação da imagem**  
  
     **manifesto de implantação de -s de imagem - cf certfile - pwd senha**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Para incluir um arquivo de dados usando MageUI.exe  
  
1.  Adicione o arquivo de dados para o diretório de aplicativo com o restante dos arquivos do aplicativo.  
  
2.  Normalmente, o diretório de seu aplicativo será um diretório rotulado com a versão atual da implantação — por exemplo, v 1.0.0.0.  
  
3.  Sobre o **arquivo** menu, clique em **abrir** para abrir o manifesto do aplicativo.  
  
4.  Selecione o **arquivos** guia.  
  
5.  Na caixa de texto na parte superior da guia, insira o diretório que contém os arquivos do aplicativo e, em seguida, clique em **popular**.  
  
     O arquivo de dados será exibida na grade.  
  
6.  Definir o **tipo de arquivo** valor do arquivo de dados para **dados**.  
  
7.  Salvar o manifesto do aplicativo e assinar o arquivo novamente.  
  
     MageUI.exe solicitará que você assinar novamente o arquivo.  
  
8.  Assinar novamente o manifesto de implantação  
  
     Você deve assinar novamente o manifesto de implantação porque o hash do manifesto do aplicativo foi alterado.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)