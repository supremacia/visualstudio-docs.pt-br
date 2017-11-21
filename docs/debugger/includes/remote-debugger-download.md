---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: dcac05939cd7f16de3bc5b6748134b52ac4f80d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
1.  No dispositivo ou servidor máquina que você deseja depurar (em vez do computador executando o Visual Studio), obtenha a versão correta das ferramentas remotas.

    |Versão|Link|Observações|
    |-|-|-|
    |Visual Studio 2017 atualização 4|[Ferramentas remotas](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Sempre Baixe a versão correspondente de seu sistema operacional do dispositivo (x86 ou x64). Para navegadores mais antigos, use esses links diretos: [ferramentas remotas (x64)](https://go.microsoft.com/fwlink/?LinkId=746570&clcid=0x409) e [ferramentas remotas (x86)](https://go.microsoft.com/fwlink/?LinkId=746569&clcid=0x409).|
    |Visual Studio de 2017 (antiga)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Se solicitado, ingressar no grupo de recursos básicos de desenvolvimento do Visual Studio livre ou você pode entrar com uma assinatura válida do Visual Studio. Em seguida, reabra o link se necessário.|
    |Visual Studio 2015 Atualização 3|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingressar no grupo de recursos básicos de desenvolvimento do Visual Studio livre ou você pode entrar com uma assinatura válida do Visual Studio. Em seguida, reabra o link se necessário.|
    |Visual Studio 2015 (antiga)|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se solicitado, ingressar no grupo de recursos básicos de desenvolvimento do Visual Studio livre ou você pode entrar com uma assinatura válida do Visual Studio. Em seguida, reabra o link se necessário.|
    |Visual Studio 2013|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Baixar página na documentação do Visual Studio 2013|
    |Visual Studio 2012|[Ferramentas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Baixar página na documentação do Visual Studio 2012|
  
2.  Na página de download, escolha a versão das ferramentas que corresponde ao seu sistema operacional (x 86, x64 ou ARM) e baixar as ferramentas remotas.
  
    > [!IMPORTANT]
    >  Recomendamos que você instale a versão mais recente das ferramentas remotas que corresponde à sua versão do Visual Studio. Versões não correspondentes não são recomendadas. Além disso, você deve instalar as ferramentas remotas que têm a mesma arquitetura do sistema operacional no qual você deseja instalá-lo. Em outras palavras, se você quiser depurar um aplicativo de 32 bits em um computador remoto executando um sistema operacional de 64 bits, você deve instalar a versão de 64 bits das ferramentas remotas no computador remoto. 
    >   
    >  Superfície 3 alternado do ARM para x64 arquitetura. Uma versão ARM das ferramentas remotas não está disponível para o Visual Studio de 2017. Para Visual Studio 2015, localize a versão do ARM no download RTW de 2015 do Visual Studio.
  
3.  Quando você terminar de baixar o arquivo executável, vá para a próxima seção e siga as instruções de instalação.

Se você tentar copiar o depurador remoto (msvsmon.exe) para o computador remoto e executá-lo, esteja ciente de que o **Assistente de configuração do depurador remoto** (**rdbgwiz.exe**) é instalado apenas quando você baixar o ferramentas. Talvez seja necessário usar o Assistente para configuração mais tarde, especialmente se você deseja que o depurador remoto para ser executado como um serviço. Para obter mais informações, consulte [(opcional) configurar o depurador remoto como um serviço](../../debugger/remote-debugging.md#bkmk_configureService).