---
title: Visual Studio e Xamarin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: e550d7f6220d4d555d8427bcb1c2a3e814a4f5c3
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio e Xamarin
O Xamarin é uma plataforma de desenvolvimento de aplicativos móveis para compilar aplicativos nativos iOS, Android e Windows de uma base C#/.NET comum, atingindo 75% a quase 100% de reutilização de código entre plataformas. Aplicativos gravados com Xamarin e C# têm acesso completo às APIs da plataforma subjacente e a capacidade de compilar interfaces do usuário nativas e compilar para pacotes específicos de plataforma, portanto não há muito impacto no desempenho de tempo de execução. (Observação: o Xamarin também dá suporte a F#, mas essa documentação se concentra somente em C#. No momento, não há suporte para o Visual Basic.)  
  
 Melhor ainda, os desenvolvedores familiarizados com C#, .NET e Visual Studio aproveitarão o mesmo o poder e a produtividade ao trabalhar com o Xamarin para aplicativos móveis, incluindo a depuração remota em dispositivos Android, iOS e Windows — sem precisar aprender idiomas de codificação nativa, como Objective-C ou Java. Portanto, é uma pequena surpresa que vários aplicativos de alto desempenho com interfaces do usuário lindas, como NASCAR, Aviva e MixRadio, tenham sido criados usando o Xamarin.  
  
 Esta documentação ajuda você a avaliar os recursos completos do **Visual Studio com Xamarin** para compilar essas experiências.  
  
-   Comece com [Configuração e instalação](../cross-platform/setup-and-install.md), um processo que levará um tempo (normalmente 2 a 4 horas dependendo da velocidade da sua conexão de Internet, o que você já instalou e as opções selecionadas).  
  
-   Enquanto os instaladores estão em execução, você pode [Saber mais sobre desenvolvimento móvel com Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md), que informa a natureza do Xamarin, compara o Xamarin.Forms a interface do usuário nativa e muito mais.  
  
-   Depois que a instalação for concluída, [Verifique seu ambiente Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
-   Conclua ao passar pelo tutorial [Aprendendo as noções básicas de build de aplicativos com o Xamarin.Forms no Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
 Você pode trabalhar com todos os recursos de Xamarin por meio de [qualquer edição do Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional e Enterprise). Observe também que a partir de 31 de março de 2016, o Xamarin está incluído em todas as edições do Visual Studio 2015 e não exige uma licença separada. Para o Visual Studio 2013, você pode instalar o Xamarin separadamente, conforme o tópico [Configuração e instalação](../cross-platform/setup-and-install.md) descreve.  
  
> [!NOTE]
>  Essas instruções descrevem a configuração de computador mais fácil e direta para aqueles que têm uma tela de fundo do Windows e o Visual Studio. Com essa configuração, a experiência geral de desenvolvimento é simplificada porque você só precisa interagir com o Mac para usar o simulador de iOS e dispositivos vinculados. Se, você vem em vez disso, você usar uma tela de fundo do Mac, recomendamos a execução do Visual Studio no Parallels/VMWare ou o uso do Xamarin Studio Community. Consulte [Configuração, instalação e verificações para usuários do Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) Microsoft Docs.  
  
> [!NOTE]
>  Se você estiver procurando por uma solução de desenvolvimento de multiplataforma com base em HTML e CSS, confira as Ferramentas do Visual Studio para Apache Cordova conforme descrito em [Desenvolvimento de Multiplataforma no Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).