---
title: Aplicativos de servidor SDI | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: feec570217240c7b7dd7d71b7f40987b756869de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sdi-server-applications"></a>Aplicativos de servidor SDI
Se você estiver depurando um aplicativo de servidor SDI, você deve especificar `/Embedding` ou `/Automation` no **argumentos de linha de comando** propriedade o *projeto* caixa de diálogo páginas de propriedades para C/C++, c#, ou Projetos do Visual Basic.  
  
 Com esses argumentos de linha de comando, o depurador pode iniciar o aplicativo de servidor como se tivesse sido iniciado de um contêiner. Iniciar o contêiner do Gerenciador de Programas ou do Gerenciador de Arquivos fará com que o contêiner use a instância do servidor iniciada no depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Localizando a propriedade Argumentos de Linha de Comando  
 Para acessar o *projeto* caixa de diálogo páginas de propriedades, clique em seu projeto no Gerenciador de soluções e escolha Propriedades no menu de atalho. Para localizar a propriedade Argumentos de linha de comando, expanda a categoria Propriedades de Configuração e clique na página Depuração.  
  
## <a name="see-also"></a>Consulte também  
 [COM e ActiveX depuração](../debugger/com-and-activex-debugging.md)   
 [Como depurar servidores COM](../debugger/how-to-debug-com-servers.md)