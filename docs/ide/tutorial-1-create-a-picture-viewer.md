---
title: 'Tutorial 1: criar um visualizador de imagens | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: "19"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b0537b1f335d46854dd43727ade695909db421ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutorial 1: Criar um visualizador de imagens
Neste tutorial, você cria um programa que carrega uma imagem de um arquivo e a exibe em uma janela. Você aprende a arrastar controles como botões e caixas de imagem no formulário, definir as respectivas propriedades e usar contêineres para redimensionar suavemente o formulário. Você também pode começar a escrever código. Você aprenderá como:  
  
-   Crie um novo projeto.  
  
-   Testar (depurar) um aplicativo.  
  
-   Adicionar controles básicos como caixas de seleção e botões para um formulário.  
  
-   Posicionar controles em um formulário usando layouts.  
  
-   Adicionar as caixas de diálogo **Abrir Arquivo** e **Cor** a um formulário.  
  
-   Escrever código usando o IntelliSense e trechos de código.  
  
-   Escrever métodos de manipulador de eventos.  
  
 Quando você terminar, seu programa será como a imagem a seguir.  
  
 ![Imagem que você cria neste tutorial](../ide/media/express_pictureviewerdone.png "Express_PictureViewerDone")  
Mostre que você cria neste tutorial  
  
 Para baixar uma versão concluída do exemplo, consulte [Exemplo de tutorial completo do Visualizador de Imagens](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![link para o vídeo](../data-tools/media/playvideo.gif "PlayVideo")Para ver uma versão em vídeo deste tópico, consulte [Como eu faço para: criar um visualizador de imagens no Visual Basic?](http://go.microsoft.com/fwlink/?LinkId=205207) ou [Como eu faço para: criar um visualizador de imagens em C#?](http://go.microsoft.com/fwlink/?LinkId=205198).  
  
> [!NOTE]
>  Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio. O Visual C# e o Visual Basic são abordados neste tutorial, portanto concentre-se nas informações específicas da linguagem de programação que você está usando.  
>   
>  Para ver o código para Visual Basic, escolha a guia **VB** na parte superior dos blocos de código e, para ver o código para Visual C#, escolha a guia **C#**. Se estiver interessado em aprender sobre o Visual C++, consulte [Introdução](../ide/getting-started-with-cpp-in-visual-studio.md) e [Tutorial da linguagem C++](http://www.cplusplus.com/doc/tutorial/).  
>   
>  Se você estiver interessado em aprender a escrever aplicativos UWP do Visual C# ou Visual Basic, consulte [Criar aplicativos UWP](https://developer.microsoft.com/windows/apps).
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Etapa 1: criar um projeto de aplicativo do Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Comece criando um projeto de aplicativo do Windows Forms.|  
|[Etapa 2: executar o programa](../ide/step-2-run-your-program.md)|Execute o programa de aplicativo do Windows Forms que você criou na etapa anterior.|  
|[Etapa 3: definir as propriedades do formulário](../ide/step-3-set-your-form-properties.md)|Altere a aparência do seu formulário usando a janela **Propriedades**.|  
|[Etapa 4: definir o layout do formulário com um controle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Adicione um controle `TableLayoutPanel` ao seu formulário.|  
|[Etapa 5: adicionar controles ao formulário](../ide/step-5-add-controls-to-your-form.md)|Adicione controles, como um controle `PictureBox` e um controle `CheckBox`, ao seu formulário. Adicionar botões ao seu formulário.|  
|[Etapa 6: nomear os controles de botão](../ide/step-6-name-your-button-controls.md)|Renomear os botões a algo mais significativo.|  
|[Etapa 7: adicionar componentes de diálogo ao formulário](../ide/step-7-add-dialog-components-to-your-form.md)|Adicione um componente **OpenFileDialog** e um componente **ColorDialog** ao seu formulário.|  
|[Etapa 8: escrever código para o manipulador de eventos do botão Mostrar uma Imagem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Escrever código usando a ferramenta do IntelliSense.|  
|[Etapa 9: examinar, comentar e testar o código](../ide/step-9-review-comment-and-test-your-code.md)|Revise e teste seu código. Adicionar comentários quando necessário.|  
|[Etapa 10: escrever código para botões adicionais e uma caixa de seleção](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Escrever código para tornar outros botões e uma caixa de seleção trabalhar usando o IntelliSense.|  
|[Etapa 11: executar o programa e experimentar outros recursos](../ide/step-11-run-your-program-and-try-other-features.md)|Execute o programa e defina a cor do plano de fundo. Tente outros recursos, como alterar cores, fontes, e bordas.|