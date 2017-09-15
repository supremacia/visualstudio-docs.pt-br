---
title: "Depurar estilos CSS com o Explorador do DOM | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Estilos CSS [aplicativos da Windows Store], depuração"
  - "Depuração de regras de CSS [aplicativos da Windows Store]"
  - "depuração de CSS [aplicativos da Windows Store]"
  - "depuração de regras CSS [aplicativos da Windows Store]"
  - "depuração de HTML [aplicativos da Windows Store]"
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 44
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar estilos CSS com o Explorador do DOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Quando você estiver depurando aplicativos da Windows Store, aplicativos da Windows Phone Store e aplicativos criados usando o Visual Studio Tools for Apache Cordova, você pode exibir e alterar regras de CSS para elementos DOM selecionados e seus elementos filho.  
  
 As guias **Estilos** e **Computado** do Explorador do DOM mostram as regras de CSS que se aplicam a um elemento selecionado. As regras são exibidas na ordem de sua especificidade de acordo com as regras de precedência de CSS. As regras na parte superior de um seletor ou estilo de uma guia \(as regras mais específicas\) são as últimas a serem aplicadas ao elemento selecionado, e as regras na parte inferior de um seletor ou estilo são as primeiras a serem aplicadas. Quando as regras são aplicadas, elas substituem as regras aplicadas anteriormente.  
  
 As guias **Estilos**, **Computado** e **Alterações** fornecem exibições diferentes de informações de estilo.  
  
-   Use a guia **Estilos** para exibir as regras organizadas por nome do seletor de CSS, como `html, body`. Você também pode usar essa guia para habilitar ou desabilitar estilos específicos, editar valores manualmente e ver os resultados imediatos dessas alterações.  
  
-   Use a guia **Calculado** para exibir os valores calculados de um estilo. Por exemplo, se você definir um tamanho para 1em, o valor calculado pelo Internet Explorer poderá ser 16px. Os estilos nessa guia estão organizados por nome de estilo, como `height`. Você também pode usar essa guia para habilitar ou desabilitar estilos específicos, editar valores manualmente e ver os resultados imediatos dessas alterações.  
  
    > [!NOTE]
    >  No Visual Studio 2013 Update 2, as informações fornecidas na guia **Rastrear** foram mescladas com a guia **Computado** e a guia **Rastrear** foi removida.  
  
-   Use o **alterações** guia \(apenas para aplicativos da Windows Store e Windows Phone Store\) para identificar e rastrear os estilos CSS alterados durante uma sessão de depuração.  
  
> [!TIP]
>  As mudanças que você faz nos estilos nas guias **Estilos** e **Computado** não são permanentes. Elas são perdidas quando você interrompe a depuração. Para alterar o código\-fonte e recarregar páginas sem interromper e reiniciar o depurador, atualize seu aplicativo usando o  ![Atualizar botão de aplicativo do Windows](~/debugger/media/js_refresh.png "JS\_Refresh") botão \(**Atualizar aplicativo do Windows**\) sobre o **Depurar** barra de ferramentas \(somente para aplicativos da Windows Store e Windows Phone Store\). Para saber mais, veja [Atualizar um aplicativo \(JavaScript\)](../debugger/refresh-an-app-javascript.md).  
  
## Exemplo de correção de uma regra de CSS  
 Este exemplo mostra como inspecionar regras de CSS e depurar um problema de estilo. Por exemplo, vamos supor que você mude a cor de uma fonte usada para exibir títulos de grupo no modelo de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] Aplicativo de Separação.  
  
> [!NOTE]
>  Este exemplo mostra um aplicativo da Windows Store, mas todos os recursos do Explorador do DOM mostrados também se aplicam a um aplicativo do Windows Phone Store e, com exceção da guia alterações, um aplicativo criado usando o Visual Studio Tools para o Apache Cordova.  
  
#### Para exibir e alterar regras de CSS  
  
1.  No Visual Studio, crie um novo aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] usando JavaScript e HTML no modelo de projeto de Aplicativo de Separação.  
  
2.  No **Gerenciador de Soluções**, abra o arquivo items.css. \(Você pode encontrar o arquivo items.css na pasta de páginas.\)  
  
3.  Substitua o código de CSS a seguir:  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; }  
    ```  
  
     com isso:  
  
    ```css  
    .itemspage .itemslist .item { -ms-grid-columns: 1fr; -ms-grid-rows: 1fr 90px; display: -ms-grid; height: 250px; width: 250px; color: #ff6a00; }  
    ```  
  
     Isso adiciona um estilo que especifica a cor \#ff6a00 \(laranja\) para cada item na lista. O seletor de CSS, `.itemspage .itemslist .item`, indica um conjunto de nomes de classe para elementos DIV em items.html, que aparecem como elementos aninhados em DOM ativos. O elemento DIV `item` especifica os itens de lista.  
  
4.  Selecione **Simulador** na lista suspensa na barra de ferramentas **Depurar** \(**Computador Local** é o valor padrão\).  
  
     ![Select debug target list](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
5.  Pressione F5 para executar o aplicativo no modo de depuração.  
  
     Quando o carregamento do arquivo terminar, observe os títulos dos itens de lista, como **Título do Grupo: 1**. A cor não foi alterada. Assim, a tentativa de aplicar uma cor laranja aos títulos não funcionou. Vamos entender o que deu errado e corrigir usando as guias CSS no Explorador de DOMs.  
  
    > [!TIP]
    >  Depois que o aplicativo aparecer no Simulador, posicione o Simulador ao lado da janela do Visual Studio para que seja possível ver imediatamente os resultados das seleções e alterações feitas em estilos CSS.  
  
6.  Alterne para o Visual Studio e clique em **Selecionar Elemento** no Explorador do DOM \(ou pressione Ctrl \+ B\). O modo de seleção muda, permitindo que você selecione um item clicando nele, e o aplicativo é colocado em primeiro plano. O modo é revertido após um único clique. Aqui está o botão **Selecionar Elemento**.![Selecione o elemento botão no Explorer do DOM](~/debugger/media/js_dom_select_element_button.png "JS\_DOM\_Select\_Element\_Button")  
  
    > [!TIP]
    >  Você também pode selecionar elementos HTML diretamente no Explorador de DOMs. Para obter mais informações sobre como selecionar elementos, consulte [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7.  No Simulador, focalize o título do primeiro item na lista, **Título do Grupo: 1**, no painel esquerdo da página inicial. O título é realçado, conforme mostrado aqui:  
  
     ![Usando o botão do elemento Select](~/debugger/media/js_css_select_element.png "JS\_CSS\_Select\_Element")  
  
    > [!NOTE]
    >  O Emulador do Windows Phone só permite destacar os elementos parcialmente ao focalizá\-los.  
  
8.  Clique no título destacado. O Explorador de DOMs seleciona automaticamente o elemento HTML correspondente, que é semelhante a este:  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Quando você seleciona o elemento H4 no Explorador do DOM, as guias do Explorador do DOM mostram as regras associadas ao elemento H4. A guia **Calculado** é mostrada aqui, com a propriedade de `color` aberta:  
  
     ![Guia de estilos de rastreamento no Explorer do DOM](~/debugger/media/js_css_styles.png "JS\_CSS\_Styles")  
  
     Essa exibição fornece informações úteis sobre as regras que estão associadas ao estilo de `color`, como indicado a seguir:  
  
    -   O seletor de CSS que alteramos no items.css, `.itemspage .itemslist .item`, não está sendo usado no cálculo de estilo final \(aparece como texto tachado\). Várias outras ocorrências do estilo de `color` também não estão sendo usadas.  
  
        > [!TIP]
        >  No caso de nomes mais extensos do seletor, o nome completo aparece em uma dica de ferramenta.  
  
    -   O valor computado de CSS final, `rgba(255, 255, 255, 0.87)`, é definido especialmente para o seguinte seletor de CSS: `.itemspage .itemslist .item .item-overlay .item-title`, que também é definido em items.css.  
  
        > [!TIP]
        >  Agora que sabemos onde a cor do título está definida, também sabemos onde podemos alterá\-la. No entanto, também podemos testar as alterações no Explorador do DOM sem atualizar o aplicativo, como mostrado nas etapas restantes.  
  
9. Desmarque a caixa de seleção da primeira ocorrência do estilo de `color`, que é para o seletor `.itemspage .itemslist .item .item-overlay .item-title`. Agora, no Simulador, você verá que a cor dos títulos dos itens mudará para laranja, como pretendíamos, e o seletor que modificamos no CSS, `.itemspage .itemslist .item`, não será mais substituído \(isto é, não terá mais texto tachado aplicado\). Esta é a guia **Computado** depois que desmarcarmos a caixa de seleção.  
  
     ![The Computed tab after updating the CSS style](~/debugger/media/js_css_styles_fixed.png "JS\_CSS\_Styles\_Fixed")  
  
10. Selecione a guia **Alterações**.  
  
     Use a guia **Alterações** para identificar e rastrear alterações de estilos que você realizou durante uma sessão de depuração. A imagem a seguir mostra o seletor `.itemspage .itemslist .item .item-overlay .item-title` na guia **Alterações**, que foi substituído.  
  
     ![Changes tab of the DOM Explorer](~/debugger/media/js_css_styles_changes.png "JS\_CSS\_Styles\_Changes")  
  
11. Você também pode editar manualmente os valores de estilo CSS e ver o resultado imediato usando a guia **Estilos**.  
  
12. Selecione a guia **Estilos**.  
  
13. Abra o seletor de estilo de `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Selecione a primeira ocorrência do estilo de `color` e clique duas vezes no valor de propriedade `rgb(255, 255, 255, 0.87)`.  
  
15. Use o teclado para modificar esse valor. Altere\-o para `rgb(255, 255, 0, 0.87)` e pressione Enter. As cores dos títulos do item no Simulador mudam para amarelo.  
  
16. Para fazer alterações no arquivo CSS de origem, clique no link **items.css** da guia **Estilos**. Isso abre o arquivo items.css, no qual é possível alterar o valor do estilo de `color` no código do aplicativo. Para atualizar o aplicativo sem interromper e reiniciar o depurador, clique o  ![Atualizar botão de aplicativo do Windows](~/debugger/media/js_refresh.png "JS\_Refresh") \(**Atualizar aplicativo do Windows**\) botão o **Depurar** barra de ferramentas.  
  
## Consulte também  
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Depurar o layout com o Explorador do DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Exibir ouvintes de eventos DOM](../debugger/view-dom-event-listeners.md)   
 [Suporte ao produto e acessibilidade](http://go.microsoft.com/fwlink/?LinkId=253502)