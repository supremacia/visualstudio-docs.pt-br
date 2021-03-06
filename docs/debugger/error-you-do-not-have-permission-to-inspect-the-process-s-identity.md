---
title: "Erro: Você não tem permissão para inspecionar o processo de &#39; identidade de s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f51087d4f7882c34826942a898328640107a5ac6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Erro: Você não tem permissão para inspecionar o processo de &#39; identidade s
Você não tem permissão para inspecionar a identidade do processo. Isto pode ocorrer devido à configuração do sistema.  
  
 O depurador não pôde inspecionar a identidade do processo, que são informações necessárias para depuração. A causa mais provável é que os Serviços de Terminal estão sendo desabilitados. O serviço dos Serviços de Terminal é habilitado por padrão. Siga estas etapas para habilitá-lo novamente.  
  
### <a name="to-enable-terminal-services"></a>Para habilitar Serviços de Terminal  
  
1.  Clique em **iniciar** e, em seguida, escolha **painel de controle**.  
  
2.  No painel de controle, escolha **alternar para modo de exibição clássico**, se necessário e, em seguida, clique duas vezes em **ferramentas administrativas**.  
  
3.  No **ferramentas administrativas** janela, clique duas vezes em **gerenciamento do computador**.  
  
4.  Na janela de gerenciamento do computador, expanda o **serviços e aplicativos** nó.  
  
5.  Sob o **serviços e aplicativos**, clique em **serviços**.  
  
     Uma lista de serviços aparece no painel direito.  
  
6.  No **serviços** lista, clique no **dos serviços de Terminal** e, em seguida, escolha **propriedades**.  
  
7.  No **propriedades de serviços de Terminal** janela, vá para o **geral** guia e defina **o tipo de inicialização** para **Manual**.  
  
8.  Clique em **OK**.  
  
9. Reinicie o computador.  
  
     Esse procedimento não habilita automaticamente a Área de Trabalho Remota. Se quiser habilitar a Área de Trabalho Remota no computador, execute o seguinte procedimento adicional.  
  
### <a name="to-enable-remote-desktop"></a>Para habilitar a Área de Trabalho Remota  
  
1.  Clique em **iniciar** e, em seguida, clique com botão direito **meu computador**.  
  
2.  Escolha **propriedades**.  
  
     O **propriedades do sistema** janela é exibida.  
  
3.  Clique em **remoto**.  
  
4.  Em **área de trabalho remota**, selecione **permitem que os usuários se conectem remotamente a este computador**.  
  
5.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)