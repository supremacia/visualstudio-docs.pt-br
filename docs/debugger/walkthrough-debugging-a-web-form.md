---
title: "Passo a passo: Depurando um formulário da Web | Microsoft Docs"
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
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 842b52d063b5de701c74501410e3249da7358776
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-a-web-form"></a>Instruções passo a passo: depurando um formulário Web
As etapas deste passo a passo mostram como depurar um aplicativo Web do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], também conhecido como um Web Form. Ele mostra como iniciar e parar a execução, definir pontos de interrupção e examinar variáveis no **inspecionar** janela.  
  
> [!NOTE]
>  Para concluir este passo a passo, você deverá ter privilégios de administrador no computador do servidor. Por padrão, o processo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], aspnet_wp.exe ou w3wp.exe, é executado como um processo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Para depurar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], você deverá ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] é executado. Para obter mais informações, consulte [requisitos de sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
 As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-create-the-web-form"></a>Para criar o Web Form  
  
1.  Se você já tiver uma solução aberta, feche-a.  
  
2.  Sobre o **arquivo** menu, clique em **novo**e, em seguida, clique em **Site da Web**.  
  
     O **novo Site** caixa de diálogo é exibida.  
  
3.  No **modelos** painel, clique em **Site da Web ASP.NET**.  
  
4.  Sobre o **local** linha, clique em **HTTP** na lista e, na caixa de texto, digite **http://localhost/WebSite**.  
  
5.  No **idioma** lista, clique em **Visual C#** ou **Visual Basic**.  
  
6.  Clique em **OK**.  
  
     O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria um novo projeto e exibe o código-fonte HTML padrão. Ele também cria um novo diretório virtual chamado **site** em **Default Web Site** no IIS.  
  
7.  Clique o **Design** guia na margem inferior.  
  
8.  Clique o **caixa de ferramentas** guia na margem esquerda ou selecione-o no **exibição** menu.  
  
     O **caixa de ferramentas** é aberto.  
  
9. No **caixa de ferramentas**, clique no **botão** controlar e adicioná-lo à superfície de design principal, Default.aspx.  
  
10. No **caixa de ferramentas**, clique no **Textbox** controlar e arraste o controle para a superfície de design principal Default.aspx.  
  
11. Clique duas vezes no controle de botão que você removeu.  
  
     Isso leva à página de código: Default.aspx.cs para C# ou Default.aspx.vb para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. O cursor deve estar na função `Button1_Click`.  
  
12. Na função `Button1_Click`, adicione o seguinte código:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. No menu **Compilar**, clique em **Compilar Solução**.  
  
     O projeto deve ser compilado sem erros.  
  
     Agora, você está pronto para iniciar a depuração.  
  
### <a name="to-debug-the-web-form"></a>Para depurar o Web Form  
  
1.  Na janelafault.aspx.cs ou Default.aspx.vb, clique na margem esquerda na mesma linha que o texto que você adicionou:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Um ponto vermelho aparece e o texto da linha é realçado em vermelho. O ponto vermelho representa um ponto de interrupção. Quando você executa o aplicativo no depurador, o depurador interromperá a execução nesse local quando o código é atingido. Você pode exibir o estado do aplicativo e depurá-lo. Para obter mais informações, consulte [pontos de interrupção](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  No menu **Depuração**, clique em **Iniciar Depuração**.  
  
3.  O **depuração habilitada não** caixa de diálogo é exibida. Selecione **modificar o arquivo Web. config para habilitar a depuração** opção e clique em **Okey**.  
  
     O Internet Explorer inicia e exibe a página recém-criada.  
  
4.  No Internet Explorer, clique no botão.  
  
     No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], essa opção leva você à linha onde você define o ponto de interrupção na página de código Default.aspx.cs ou Default.aspx.vb. Essa linha deve ser realçada em amarelo. Agora você pode exibir as variáveis em seu aplicativo e controlar sua execução. Seu aplicativo para a execução e aguarda você enviar um comando.  
  
5.  No **depurar** menu, clique em **Windows**, em seguida, clique em **inspecionar**e, em seguida, clique em **inspecionar 1**.  
  
6.  No **inspecionar** , digite **TextBox1**.  
  
     O **inspecionar** janela mostra o valor da variável `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Sobre o **depurar** menu, clique em **passar por**.  
  
     O valor de `TextBox1.Text` alterações no **inspecionar** janela para ler:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Sobre o **depurar** menu, clique em **continuar**.  
  
9. No Internet Explorer, clique no botão novamente.  
  
     A execução para no ponto de interrupção novamente.  
  
10. Na janelafault.aspx.cs ou Default.aspx.vb, clique no ponto vermelho na margem esquerda:  
  
     Isso remove o ponto de interrupção.  
  
11. Sobre o **depurar** menu, clique em **parar depuração**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Para anexar ao Web Form para depurar  
  
1.  No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode anexar o depurador a um processo em execução. Para obter uma depuração mais efetiva, compile o executável como arquivos da versão de depuração com símbolo (PDB).  
  
2.  Na janelafault.aspx.cs ou Default.aspx.vb, clique na margem esquerda para novamente definir um ponto de interrupção na linha adicionada:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Sobre o **depurar** menu, clique em **Start Without Debugging**.  
  
     O Web Form começa a ser executado no Internet Explorer, mas o depurador não está anexado.  
  
4.  Anexe ao processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Para obter mais informações, consulte [depuração de aplicativos de Web implantados](../debugger/debugging-deployed-web-applications.md).  
  
5.  No Internet Explorer, clique no botão no seu formulário.  
  
     No [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você deve atingir o ponto de interrupção em Default.aspx.cs, Default.aspx.vb ou Default.aspx.  
  
6.  Quando tiver terminado de depuração, no **depurar** menu, clique em **parar depuração**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)