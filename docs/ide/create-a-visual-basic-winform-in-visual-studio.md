---
title: Criar um aplicativo do Windows Forms no Visual Studio com o Visual Basic | Microsoft Docs
description: Aprenda o passo a passo de como criar um aplicativo do Windows Forms no Visual Studio com o Visual Basic.
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 592ad202ca41792c6a73a77b7c01bab71fdbcdc7
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2018
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Criar um aplicativo do Windows Forms no Visual Studio com o Visual Basic
Nesta introdução curta ao IDE (Ambiente de Desenvolvimento Integrado) do Visual Studio, você criará um aplicativo simples do Visual Basic que tem uma UI (interface do usuário) baseada no Windows.

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalá-lo gratuitamente.

## <a name="create-a-project"></a>Criar um projeto
Primeiro, você criará um projeto de aplicativo do Visual Basic. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada.  

1. Abra o Visual Studio 2017.  

2. Na barra de menus superior, selecione **Arquivo** > **Novo** > **Projeto...**.  

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda a opção **Visual Basic** e, em seguida, escolha **Área de Trabalho Clássica do Windows**. No painel central, selecione **Aplicativo do Windows Forms (.NET Framework)**. Em seguida, dê o nome `HelloWorld` para o arquivo.  

     Se você não vir o modelo de projeto **Aplicativo do Windows Forms (.NET Framework)**, cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos...** O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de área de trabalho do .NET** e, em seguida, selecione **Modificar**.  

     ![Carga de trabalho do .NET Core no Instalador do Visual Studio](../ide/media/install-dot-net-desktop-env.png)  

## <a name="create-the-application"></a>Criar o aplicativo
Depois de selecionar o modelo de projeto do Visual Basic e nomear seu arquivo, o Visual Studio abrirá um formulário para você. Um formulário é uma interface do usuário do Windows. Vamos criar um aplicativo “Olá, Mundo” ao adicionar controles ao formulário e, então, vamos executar o aplicativo.   

### <a name="add-a-button-to-the-form"></a>Adicionar um botão no formulário  

1. Clique na **Caixa de Ferramentas** para abrir a janela suspensa da Caixa de Ferramentas.

     ![Clique na Caixa de Ferramentas para abrir a janela da Caixa de Ferramentas](../ide/media/vb-toolbox-toolwindow.png)  

     (Se você não vir a opção suspensa Caixa de Ferramentas, ela poderá ser aberta da barra de menus. Para fazer isso, clique em **Exibir** > **Caixa de Ferramentas**. Ou pressione **Ctrl**+**Alt**+**X**.)

2. Clique no ícone **Fixar** para encaixar a janela Caixa de Ferramentas.

     ![Clique no ícone Fixar para fixar a janela Caixa de Ferramentas no IDE](../ide/media/vb-pin-the-toolbox-window.png)  
3. Clique no controle **Botão** e, em seguida, arraste-o para o formulário.

     ![Adicionar um botão no formulário](../ide/media/vb-add-a-button-to-form1.png)

4. Na seção **Aparência** da janela **Propriedades**, digite “Click this” (Clique aqui) e, em seguida, pressione **Enter**.

     ![Adicionar texto no botão do formulário](../ide/media/vb-button-control-text.png)  

     (Se você não vir a janela Propriedades, ela poderá ser aberta da barra de menus. Para fazer isso, clique em **Exibir** > **Janela Propriedades**. Ou pressione **F4**.)

5. Na seção **Design** da janela **Propriedades**, altere o nome de “Button1” para “btnClickThis” e, em seguida, pressione **Enter**.

     ![Adicionar uma função ao botão no formulário](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Adicionar um rótulo ao formulário
Agora que adicionamos um controle de botão para criar uma ação, vamos adicionar um controle de rótulo para enviar o texto.

1. Selecione o controle **Rótulo** da janela Caixa de Ferramentas e, então, arraste-a para o formulário e solte-a sob o botão **Clique aqui**.

2. Na seção **Design** da janela **Propriedades**, altere o nome de “Label1” para “lblHelloWorld” e, em seguida, pressione **Enter**.

### <a name="add-code-to-the-form"></a>Adicionar código ao formulário

1. Na janela **Form1.vb &#91;Design&#93;**, clique duas vezes no botão **Clique aqui** para abrir a janela **Form1.vb**.

      (Como alternativa, você pode expandir a opção **Form1.vb** na janela **Gerenciador de Soluções** e, então, clicar em **Form1**.)

2. Na janela **Form1.vb**, entre as linhas **Private Sub** e **End Sub**, digite ou cole `lblHelloWorld.Text = "Hello World!"`.

     ![Adicionar código ao formulário](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Executar o aplicativo
1. Clique no botão **Iniciar** para executar o aplicativo.

     ![Clique em Iniciar para depurar e executar o aplicativo](../ide/media/vb-click-start-hello-world.png)

   Várias coisas acontecerão. No IDE do Visual Studio, a janela Ferramentas de Diagnóstico será aberta e uma janela de saída também. Mas fora do IDE, uma caixa de diálogo Form1 aparecerá. Ela incluirá seu botão **Clique aqui** e o texto que diz “Label1”.

2. Clique no botão **Clique aqui** na caixa de diálogo **Form1**. Observe que o texto “Label1” é alterado para “Olá, Mundo!”.

    ![Uma caixa de diálogo Form1 que inclui o texto Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Parabéns por concluir este guia de início rápido! Esperamos que você tenha aprendido um pouco sobre o Visual Basic e sobre o IDE do Visual Studio. Se quiser se aprofundar mais, continue com um tutorial na seção **Tutoriais** do sumário.  

## <a name="see-also"></a>Consulte também   
* [Guia de início rápido: criar um aplicativo de console no Visual Studio com o Visual Basic](quickstart-visual-basic-console.md)
* [Saiba mais sobre o Visual Basic IntelliSense](visual-basic-specific-intellisense.md)  
