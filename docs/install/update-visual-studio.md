---
title: Atualizar o Visual Studio 2017 | Microsoft Docs
description: Saiba como atualizar o Visual Studio, passo a passo.
ms.date: 03/06/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 41fc3df0806bf703385099647d2f92cfa2236051
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Atualizar o Visual Studio 2017 para a versão mais recente

Recomendamos que você atualize para a [versão mais recente](/visualstudio/releasenotes/vs2017-relnotes) do Visual Studio 2017 para que você sempre tenha os recursos, as correções e os aprimoramentos mais atualizados.

E, se você quiser experimentar algo antes de lançarmos a versão, baixe também a [versão prévia](/visualstudio/releasenotes/vs2017-preview-relnotes) da próxima versão.

> [!IMPORTANT]
> Faça logon com uma conta que tenha permissões administrativas para instalar, atualizar ou modificar o Visual Studio. Para obter mais informações, consulte [Permissões de usuário e Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Atualizar o Visual Studio 2017 versão 15.6 ou posterior

Nós simplificamos a instalação e atualizamos a experiência para facilitar o uso diretamente de dentro do IDE. Veja como atualizar da versão 15.6 e versões posteriores para as mais recentes do Visual Studio.

### <a name="use-the-notifications-hub"></a>Use o Hub de Notificações

Quando houver uma atualização, haverá um sinalizador de notificação correspondente no Visual Studio.

1. Salve o trabalho.

2. Escolha o sinalizador de notificações para abrir o Hub de **Notificações** e escolha a atualização que você deseja instalar.

  ![Atualizar o Visual Studio 2017 usando o hub de Notificação](media/vs-install-notifications-hub-15dot6.png "O hub de Notificações no Visual Studio 2017")

3. Quando a caixa de diálogo **Atualizar** for aberta, escolha **Atualizar Agora**.

    ![Atualizar o Visual Studio 2017 usando a caixa de diálogo Atualizar do hub Notificações](media/vs-update-now-from-notifications-hub.png "A caixa de diálogo Atualizar do hub Notificações no Visual Studio")

     Se uma caixa de diálogo Controle de Acesso do Usuário for aberta, escolha **Sim**. Em seguida, pode abrir uma caixa de diálogo "Aguarde" por um momento e, em seguida, o instalador do Visual Studio é aberto para iniciar a atualização.

     ![A nova experiência do instalador do Visual Studio versão 15.6](media/visual-studio-15dot6-installer.png "A nova experiência do instalador do Visual Studio versão 15.6")

     A atualização continuará. Em seguida, quando ele for concluído, o Visual Studio será reiniciado.

### <a name="use-the-ide"></a>Usar o IDE

Você pode verificar se há uma atualização e, em seguida, instalar a atualização pela barra de menus do Visual Studio.

1. Salve o trabalho.

2. Escolha **Ajuda** > **Verificar se há Atualizações**.

     ![O novo menu Ajuda no Visual Studio versão 15.6](media/vs-help-menu-check-for-updates.png "O novo menu Ajuda no Visual Studio versão 15.6")

3. Quando a caixa de diálogo **Atualizar** for aberta, escolha **Atualizar Agora**.

   A atualização continua conforme descrito na seção anterior e, em seguida, o Visual Studio é reiniciado após a atualização ser concluída com êxito.

### <a name="use-the-visual-studio-installer"></a>Usar o instalador do Visual Studio

Como nas versões anteriores do Visual Studio de 2017, você pode usar o instalador do Visual Studio para instalar uma atualização.

1. Salve o trabalho.

2. Abra o instalador. O instalador do Visual Studio pode exigir a atualização antes de continuar.

  > [!NOTE]
  > Em um computador com Windows 10, você poderá encontrar o instalador na letra **V** como o **Instalador do Visual Studio**, ou na letra **M** como o **Instalador do Microsoft Visual Studio**.

2. Na página **Produto** no instalador, procure a edição do Visual Studio instalada.

3. Se uma atualização estiver disponível, você verá um botão **Atualizar**. (Pode levar alguns segundos para o instalador determinar se uma atualização está disponível.)

  Escolha o botão **Atualizar** para instalar as atualizações.

     ![Atualizar o Visual Studio 2017 usando o Instalador do Visual Studio](media/update-visual-studio.png "Atualizar o Visual Studio 2017 usando o Instalador do Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Atualizar o Visual Studio 2017 versão 15.5 ou anterior

Se você estiver usando uma versão anterior, veja como aplicar uma atualização do Visual Studio 2017 versão 15.0 pela versão 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Atualizar usando o hub de Notificações

1. Quando houver atualizações, haverá um sinalizador de notificação correspondente no Visual Studio.

  ![Atualizar o Visual Studio 2017 usando o Hub de notificação](media/notification-flag.png "O sinalizador de Notificação de atualização no Visual Studio")

  Escolha o sinalizador de notificação para abrir o Hub de **Notificações**.

  ![Atualizar o Visual Studio 2017 usando o hub de Notificação](media/notifications-hub.png "O hub de Notificações no Visual Studio")

2. Escolha **“Atualização do Visual Studio” está disponível**, que abre a caixa de diálogo **Extensões e Atualizações**.

  ![Atualizar o Visual Studio 2017 usando o hub de Notificações](media/notifications-hub-select.png "O hub de Notificações no Visual Studio")

3. Na caixa de diálogo **Extensões e Atualizações**, escolha o botão **Atualizar**.

  ![Atualizar o Visual Studio 2017 usando o hub de Notificações](media/notifications-extensions-and-updates.png "A caixa de diálogo Extensões e Atualizações no Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Mais informações sobre as notificações do Visual Studio

O Visual Studio notifica quando uma atualização está disponível para o próprio Visual Studio ou para algum componente e também quando determinados eventos ocorrem no ambiente do Visual Studio.

* Quando o sinalizador de notificação está amarelo, há uma atualização de produto do Visual Studio disponível para instalação.
* Quando o sinalizador de notificação está vermelho, há um problema com a sua licença.
* Quando o sinalizador de notificação está preto, há mensagens opcionais ou informativas a serem examinadas.

Escolha o sinalizador de notificações para abrir o Hub de **Notificações** e selecione as notificações que você deseja modificar. Ou então, escolher ignorar ou descartar uma notificação.

 ![Exibir uma mensagem opcional ou informativa no Hub de notificação](media/notification-flag-optional.png "O sinalizador de Notificação de mensagens opcionais ou informativas no Visual Studio")

Se você optar por ignorar uma notificação, o Visual Studio parará de mostrá-la. Se você quiser redefinir a lista de notificações ignoradas, escolha o botão **Configurações** no Hub de notificações.

   ![Escolha o botão Configurações no Hub de notificações para exibir as Opções de notificação](media/vs-notifications-hub-settings-button.png "Escolha o botão Configurações no Hub de notificações para exibir as opções de notificação")

### <a name="update-by-using-the-visual-studio-installer"></a>Atualizar ao usar o Instalador do Visual Studio

1. Abra o instalador. Você precisará atualizar o instalador antes de continuar. Neste caso, você será solicitado a fazer isso.

  > [!NOTE]
  > Em um computador com Windows 10, você poderá encontrar o instalador na letra **V** como o **Instalador do Visual Studio**, ou na letra **M** como o **Instalador do Microsoft Visual Studio**.

2. Na página **Produto** no instalador, procure a edição do Visual Studio instalada.

3. Se uma atualização estiver disponível, você verá um botão **Atualizar**. (Pode levar alguns segundos para o instalador determinar se uma atualização está disponível.)

  Escolha o botão **Atualizar** para instalar as atualizações.

     ![Atualizar o Visual Studio 2017 usando o Instalador do Visual Studio](media/update-visual-studio.png "Atualizar o Visual Studio 2017 usando o Instalador do Visual Studio")

## <a name="get-support"></a>Obter suporte

Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:

* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Modificar o Visual Studio 2017](modify-visual-studio.md)
* [Desinstalar o Visual Studio 2017](uninstall-visual-studio.md)
* [Guia de Administradores do Visual Studio](visual-studio-administrator-guide.md)
