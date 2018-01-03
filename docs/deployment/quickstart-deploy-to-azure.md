---
title: "Publicar no serviço de aplicativo do Azure - Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c1fa8867c4f9ab46b50f0b2a144970d772cbd71
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publicar um aplicativo ASP.NET ou ASP.NET Core para o serviço de aplicativo do Azure usando o Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET, ASP.NET Core, Python, Node. js e .NET Core para o serviço de aplicativo do Azure.

Se você não tiver uma conta do Azure, você pode [Inscreva-se aqui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **arquivo > Novo projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)**ou (c# somente) **aplicativo Web do ASP.NET Core**e, em seguida, clique em **Okey**.

1. Escolha **MVC**, certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

1. No Gerenciador de soluções, clique com o botão direito e escolha **publicar**.

    ![Escolher publicar](../deployment/media/quickstart-publish-aspnet.png "escolher publicar")

1. No **publicar** painel, escolha **serviço de aplicativo do Microsoft Azure**.

    ![Escolha o serviço de aplicativo do Azure](../deployment/media/quickstart-publish-azure.png "escolha o serviço de aplicativo do Azure")

1. Clique em **Publicar**.

    O **criar serviço de aplicativo** caixa de diálogo é exibida.

    ![Criar serviço de aplicativo](../deployment/media/quickstart-publish-settings-app-service.png "criar serviço de aplicativo do Azure")
    
1. Se você não tiver entrado no Visual Studio, entrar e, em seguida, as configurações de serviço de aplicativo padrão preencha os campos.

    Abre a caixa de diálogo de configurações de publicação do perfil.

    ![Escolha a pasta](../deployment/media/quickstart-publish-settings-web.png "Escolher pasta")

    Na caixa de diálogo, selecione a assinatura que você está usando, selecione ou crie um grupo de recursos do Azure, etc.

1. Clique em **Criar**.

    O Visual Studio implanta o aplicativo para o serviço de aplicativo do Azure e carrega o aplicativo web no navegador.

    O resumo do **publicar** painel, você vê a URL do Site para o novo serviço de aplicativo do Azure.

## <a name="next-steps"></a>Próximas etapas

- [Implantar um aplicativo do ASP.NET Core para o Azure](https://docs.microsoft.com/en-us/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Implantação contínua do ASP.NET Core para o Azure com o Git](https://docs.microsoft.com/en-us/aspnet/core/publishing/azure-continuous-deployment)