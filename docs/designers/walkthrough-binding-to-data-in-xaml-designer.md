---
title: 'Passo a passo: associando dados no Designer XAML| Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: ef8826fd01c0eec45f2daea5900c5e440a5cebb0
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Passo a passo: associando dados no Designer XAML

No Designer XAML, você pode definir as propriedades de associação de dados usando o artboard e a janela Propriedades. O exemplo neste passo a passo mostra como associar dados a um controle. Especificamente, o procedimento mostra como criar uma classe simples de carrinho de compras com [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) chamado de `ItemCount` e associar a propriedade `ItemCount` à propriedade **Text** de um controle de [TextBlock](/uwp/api/Windows.UI.Xaml.Controls.TextBlock).

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Para criar uma classe para usar como fonte de dados

1. No menu **Arquivo**, escolha **Novo**> **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, escolha o nó **Visual C#** ou **Visual Basic**, expanda o nó **Área de Trabalho do Windows** e escolha o modelo **Aplicação WPF**.

1. Nomeie o projeto como **BindingTest** e escolha o botão **OK**.

1. Abra o arquivo MainWindow.xaml.cs (ou MainWindow.xaml.vb) e adicione o código a seguir. Em C#, adicione o código ao namespace `BindingTest` (antes do parêntese de fechamento no arquivo). No Visual Basic, adicione a nova classe.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   Esse código define o valor 0 como a contagem de item padrão usando o objeto [PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata).

1. No menu **Arquivo**, escolha **Compilar** > **Compilar Solução**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Para associar a propriedade ItemCount a um controle TextBlock

1. No Gerenciador de Soluções, abra o menu de atalho de MainWindow.xaml e escolha **Designer de Exibição**.

1. Na caixa de ferramentas, escolha um controle de [Grade](/uwp/api/Windows.UI.Xaml.Controls.Grid) e adicione-o ao formulário.

1. Com `Grid` selecionado, na janela Propriedades, clique no botão **Novo** próximo a propriedade **DataContext**.

1. Na caixa de diálogo **Selecionar Objeto**, verifique se a opção **Mostrar todos os assemblies** está desmarcada e selecione **ShoppingCart** no namespace **BindingTest**; em seguida, clique em **OK**.

     A ilustração a seguir mostra a caixa de diálogo **Selecionar Objeto** com a opção **ShoppingCart** selecionada.

     ![Caixa de diálogo Selecionar objeto](../designers/media/blendselectobject.PNG "BlendSelectObject")

1. Na **Caixa de ferramentas**, escolha um controle de `TextBlock` e adicione-o ao formulário.

1. Com o controle `TextBlock` selecionado, na janela Propriedades, escolha o marcador de propriedade à direita da propriedade **Texto** e escolha **Criar Vinculação de Dados**. (O marcador de propriedade se assemelha a uma caixa pequena.)

1. Na caixa de diálogo Criar Vinculação de Dados, na caixa **Caminho**, escolha a propriedade **ItemCount: (int32)** e, em seguida, escolha o botão **OK**.

     A ilustração a seguir mostra a caixa de diálogo **Criar Vinculação de Dados** com a propriedade **ItemCount** selecionada.

     ![caixa de diálogo Criar Vinculação de Dados](../designers/media/xaml_create_data_binding.png "xaml_create_data_binding")

1. Pressione **F5** para executar o aplicativo.

     O controle `TextBlock` deve mostrar o valor padrão de 0 como texto.

## <a name="see-also"></a>Consulte também

[Criando uma interface do usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)  
[Caixa de diálogo Adicionar Conversor de Valor](https://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)