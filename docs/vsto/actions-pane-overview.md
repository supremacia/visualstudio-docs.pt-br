---
title: "Visão geral do painel de ações | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0e3fb356c00b3e9943ba8aff696283d4c5339e18
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="actions-pane-overview"></a>Visão geral do painel Ações
  Um painel de ações é uma personalizável **ações do documento** painel de tarefas que está anexado a um documento específico do Microsoft Office Word ou pasta de trabalho do Microsoft Office Excel. Ele está hospedado dentro do painel de tarefas do Office junto com outros painéis de tarefas interna, como o **origem XML** no Excel ou o **estilos e formatação** painel de tarefas no Word. Você pode usar controles de formulários do Windows ou controles do WPF para criar a interface de usuário do painel de ações.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Você pode criar um painel de ações somente em uma personalização de nível de documento para Word ou Excel. Você não pode criar um painel de ações em um suplemento do VSTO. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  O painel de ações é diferente de painéis de tarefas personalizados. Painéis de tarefas personalizados estão associados com o aplicativo, não é um documento específico. Você pode criar painéis de tarefas personalizados no suplemento do VSTO para alguns aplicativos do Microsoft Office. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: Use WPF controles dentro de um Excel painel Ações?](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## <a name="displaying-the-actions-pane"></a>Exibir o painel de ações  
 O painel de ações é representado pela <xref:Microsoft.Office.Tools.ActionsPane> classe. Quando você cria um projeto no nível do documento, uma instância desta classe está disponível no seu código usando o `ActionsPane` campo o `ThisWorkbook` (para Excel) ou `ThisDocument` (para o Word) de classe em seu projeto. Para exibir o painel Ações, adicione um controle de formulários do Windows para o <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriedade o `ActionsPane` campo. O exemplo de código a seguir adiciona um controle chamado `actions` para o painel de ações.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
 O painel de ações se torna visível em tempo de execução assim que você adicionar um controle explicitamente a ele. Depois que o painel de ações é exibido, você pode adicionar ou remover controles em resposta a ações do usuário dinamicamente. Normalmente, você adiciona o código para exibir o painel de ações no `Startup` manipulador de eventos do `ThisDocument` ou `ThisWorkbook` para que o painel de ações é visível quando o usuário primeiro abre o documento. No entanto, você talvez queira exibir o painel de ações apenas em resposta a uma ação do usuário no documento. Por exemplo, você pode adicionar o código para o `Click` eventos de um controle no documento.  
  
### <a name="adding-multiple-controls-to-the-actions-pane"></a>Adicionando vários controles para o painel de ações  
 Se você estiver adicionando vários controles para o painel de ações, na maioria dos casos você deve agrupar os controles em um controle de usuário e, em seguida, adicione o controle de usuário para o <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propriedade. Esse processo inclui as seguintes etapas:  
  
1.  Criar a interface do usuário (IU) do painel Ações, adicionando um **controle do painel Ações** ou **controle de usuário** item ao seu projeto. Esses itens incluem um Windows Forms personalizados <xref:System.Windows.Forms.UserControl> classe. O **controle do painel Ações** e **controle de usuário** itens são equivalentes; a única diferença é o seu nome.  
  
2.  Adicionar controles de formulários do Windows para o <xref:System.Windows.Forms.UserControl> usando o designer ou escrevendo código.  
  
    > [!NOTE]  
    >  Você também pode adicionar controles do WPF para o painel de ações, adicionando um WPF <xref:System.Windows.Controls.UserControl> para formulários do Windows <xref:System.Windows.Forms.UserControl>. Para obter mais informações, consulte [usando controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Adicionar uma instância do controle de usuário personalizadas para os controles que estão contidos no `ActionsPane` campo o `ThisWorkbook` (para Excel) ou `ThisDocument` (para o Word) de classe em seu projeto.  
  
 Para obter exemplos que demonstram esse processo em mais detalhes, consulte [como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## <a name="hiding-the-actions-pane"></a>Ocultar o painel de ações  
 Embora o <xref:Microsoft.Office.Tools.ActionsPane> classe tem um <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método e uma <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propriedade, você não pode remover o painel de ações da interface do usuário usando os membros a <xref:Microsoft.Office.Tools.ActionsPane> classe em si. Chamando o <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método ou configuração o <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propriedade **false** oculta somente os controles no painel Ações; não oculta o painel de tarefas.  
  
 Para ocultar o painel de tarefas em sua solução, você tem várias opções:  
  
-   Para o Word, defina o <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> propriedade o <xref:Microsoft.Office.Interop.Word.TaskPane> objeto que representa o painel de tarefas ações do documento para **false**. O exemplo de código a seguir se destina a ser executado a partir de `ThisDocument` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  
  
-   Para Excel, defina o <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> propriedade o <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> do objeto para **false**. O exemplo de código a seguir se destina a ser executado a partir de `ThisWorkbook` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  
  
-   Para o Word ou Excel, você pode definir opcionalmente o <xref:Microsoft.Office.Core.CommandBar.Visible%2A> propriedade da barra de comandos que representa o painel de tarefas para **false**. O exemplo de código a seguir se destina a ser executado a partir de `ThisDocument` ou `ThisWorkbook` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  
  
### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Limpar o ações painel quando o documento é aberto.  
 Se o usuário salva o documento, enquanto o painel de ações está visível, o painel de ações é visível toda vez que o documento for aberto, se o painel de ações contém todos os controles ou não. Se você deseja controlar quando ele for exibido, chame o <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> método o `ActionsPane` campo o `Startup` manipulador de eventos do `ThisDocument` ou `ThisWorkbook` para garantir que o painel de ações não estiver visível quando o documento é aberto.  
  
### <a name="determining-when-the-actions-pane-is-closed"></a>Determinar quando o painel de ações está fechado  
 Não há nenhum evento que é gerado quando o painel de ações está fechado. Embora o <xref:Microsoft.Office.Tools.ActionsPane> classe tiver um <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> evento, esse evento não é gerado quando o usuário final para fechar o painel de ações. Em vez disso, esse evento é gerado quando os controles no painel de ações são ocultos por chamar o <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método ou definindo o <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propriedade **false**.  
  
 Se o usuário final fecha o painel de ações, o usuário pode exibi-la novamente, executando um dos procedimentos a seguir na interface do usuário (IU) do aplicativo.  
  
##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Para exibir o painel de ações, usando a interface do usuário do Word ou Excel  
  
1.  Na faixa de opções, clique no **exibição** guia.  
  
2.  No **Mostrar/ocultar** de grupo, clique no **ações do documento** botão de alternância.  
  
## <a name="programming-actions-pane-events"></a>Eventos de painel de ações de programação  
 Você pode adicionar vários controles de usuário para o painel de ações e, em seguida, escrever código para responder a eventos no documento mostrando e ocultando os controles de usuário. Se você mapear elementos de esquema XML para o documento, você pode mostrar determinados controles de usuário no painel Ações, sempre que o ponto de inserção está dentro de um dos elementos XML. Para obter mais informações, consulte [como: mapa de esquemas para o Word documentos dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) e [como: mapa de esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 Você também pode escrever código para responder a eventos de qualquer objeto, incluindo controle de host, aplicativo ou eventos de documento. Para obter mais informações, consulte [passo a passo: Programando contra eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## <a name="binding-data-to-controls-on-the-actions-pane"></a>Associando dados a controles no painel Ações  
 Os controles no painel Ações têm as mesmas capacidades de associação de dados de controles de formulários do Windows. Você pode vincular os controles a fontes de dados como conjuntos de dados, conjuntos de dados tipados e XML. Para obter mais informações, consulte [Vinculação de dados e Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 Você pode vincular controles no painel Ações e no documento para o mesmo conjunto de dados. Por exemplo, você pode criar uma relação mestre/detalhes entre os controles no painel Ações e os controles na planilha. Para obter mais informações, consulte [passo a passo: vinculação de dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## <a name="validating-data-in-actions-pane-controls"></a>Validando dados em controles de painel de ações  
 Se você exibir uma caixa de mensagem no <xref:System.Windows.Forms.Control.Validating> manipulador de eventos de um controle no painel Ações, o evento pode ser gerado pela segunda vez quando o foco move de controle para a caixa de mensagem. Para evitar esse problema, use um <xref:System.Windows.Forms.ErrorProvider> controle para exibir as mensagens de erro de validação.  
  
## <a name="user-control-stacking-order"></a>Controle de usuário, a ordem de empilhamento  
 Se você estiver usando vários controles de usuário, você pode escrever código para os controles de usuário no painel de ações de pilha corretamente se ela estiver encaixada verticalmente ou horizontalmente. Você pode definir a ordem de empilhamento dos controles de usuário no painel Ações, usando o <xref:Microsoft.Office.Tools.StackStyle> enumeração do <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> propriedade. Para obter mais informações, consulte [como: gerenciar o controle de Layout em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md)  
  
 O <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> propriedade pode ter o seguinte <xref:Microsoft.Office.Tools.StackStyle> valores de enumeração.  
  
|Estilo de empilhamento|Definição|  
|--------------------|----------------|  
|FromBottom|Empilhar na parte inferior do painel de ações.|  
|FromLeft|Empilhar na parte esquerda do painel de ações.|  
|FromRight|Empilhar na parte direita do painel de ações.|  
|FromTop|Empilhar na parte superior do painel de ações.|  
|Nenhum|Nenhuma ordem de empilhamento definida, a ordem é controlada pelo desenvolvedor.|  
  
 O código a seguir define o <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> propriedade para os controles de usuário da parte superior do painel de ações de pilha.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  
  
## <a name="anchoring-controls"></a>Controles de ancoragem  
 Se o usuário redimensionar o painel de ações em tempo de execução, os controles podem redimensionar com o painel de ações. Você pode usar o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade de um controle de formulários do Windows para controles de âncora para o painel de ações. Você também pode ancorar os controles de formulários do Windows para o controle de usuário da mesma maneira. Para obter mais informações, consulte [como: âncora controles nos Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
## <a name="resizing-the-actions-pane"></a>Redimensionar o painel de ações  
 Você não pode alterar diretamente o tamanho de um <xref:Microsoft.Office.Tools.ActionsPane> porque o <xref:Microsoft.Office.Tools.ActionsPane> é inserido no painel de tarefas. No entanto, você pode alterar programaticamente a largura do painel de tarefas, definindo o <xref:Microsoft.Office.Core.CommandBar.Width%2A> propriedade o <xref:Microsoft.Office.Core.CommandBar> que representa o painel de tarefas. Você pode alterar a altura do painel de tarefas se ele está encaixado na horizontal ou é flutuante.  
  
 Redimensionar programaticamente o painel de tarefas geralmente não é recomendável porque o usuário deve ser capaz de selecionar o tamanho do painel de tarefas que melhor atenda às suas necessidades. No entanto, se você precisa redimensionar a largura do painel de tarefas, você pode usar o código a seguir para alcançar essa tarefa.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  
  
## <a name="repositioning-the-actions-pane"></a>Reposicionar o painel de ações  
 Não é possível reposicionar o <xref:Microsoft.Office.Tools.ActionsPane> porque ele é inserido no painel de tarefas. No entanto, você pode mover programaticamente o painel de tarefas, definindo o <xref:Microsoft.Office.Core.CommandBar.Position%2A> propriedade o <xref:Microsoft.Office.Core.CommandBar> que representa o painel de tarefas.  
  
 Reposicionar programaticamente o painel de tarefas geralmente não é recomendável porque o usuário deve ser capaz de escolher a posição do painel de tarefas na tela que melhor atenda às suas necessidades. No entanto, se você deve mover o painel de tarefas para uma posição específica, você pode usar o código a seguir para alcançar essa tarefa.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Os usuários finais podem reposicionar o painel de tarefas manualmente a qualquer momento. Não há nenhuma maneira de garantir que o painel de tarefas permanecerá encaixado na posição em que você indique programaticamente. No entanto, você pode verificar as alterações de orientação e certifique-se de que os controles no painel Ações estão empilhados na direção certa. Para obter mais informações, consulte [como: gerenciar o controle de Layout em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Definindo o <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> e <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> propriedades do <xref:Microsoft.Office.Tools.ActionsPane> não altera sua posição porque o <xref:Microsoft.Office.Tools.ActionsPane> objeto é inserido no painel de tarefas.  
  
 Se o painel de tarefas não estiver encaixado, você pode definir o <xref:Microsoft.Office.Core.CommandBar.Top%2A> e <xref:Microsoft.Office.Core.CommandBar.Left%2A> propriedades da <xref:Microsoft.Office.Core.CommandBar> que representa o painel de tarefas. O código a seguir move um painel de tarefas não encaixada para o canto superior esquerdo do documento.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  
  
## <a name="see-also"></a>Consulte também  
 [Usando controles WPF em soluções do Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Como: adicionar um painel de ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Passo a passo: Inserindo texto em um documento de um painel de ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Passo a passo: Associando dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Passo a passo: Associando dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Como: gerenciar o controle Layout em painéis de ações](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Instruções passo a passo: inserindo texto em um documento de um painel Ações](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  