---
title: "Data de criação. Arquivos de VSCT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa274c807aaa1ed212a7b283a35e510615561eb5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-vsct-files"></a>Data de criação. VSCT arquivos
Este documento mostra como criar um arquivo. VSCT para adicionar itens de menu, barras de ferramentas e outros elementos de interface de usuário para o ambiente de desenvolvimento integrado (IDE) do Visual Studio. Quando você adiciona elementos de interface do usuário para um pacote do Visual Studio (VSPackage) que ainda não tiver um arquivo. VSCT, siga estas etapas.  
  
 Para novos projetos, é recomendável que você use o modelo de pacote do Visual Studio porque ele gera um arquivo. VSCT que, dependendo de suas seleções, já tem os elementos necessários para um comando de menu, uma janela de ferramenta ou um editor personalizado. Você pode modificar este arquivo. VSCT para atender aos requisitos do seu VSPackage. Para obter mais informações sobre como modificar um arquivo. VSCT, consulte os exemplos em [estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Criando o arquivo  
 Criar um arquivo. VSCT essas fases: criar a estrutura de arquivos e recursos, declarar os elementos da interface do usuário, colocar os elementos de interface do usuário no IDE e adicionar qualquer comportamento especializado.  
  
### <a name="file-structure"></a>Estrutura de arquivos  
 A estrutura básica de um arquivo. VSCT é um [CommandTable](../../extensibility/commandtable-element.md) elemento raiz que contém um [comandos](../../extensibility/commands-element.md) elemento e um [símbolos](../../extensibility/symbols-element.md) elemento.  
  
##### <a name="to-create-the-file-structure"></a>Para criar a estrutura de arquivo  
  
1.  Adicionar um arquivo. VSCT ao seu projeto, seguindo as etapas em [como: criar um. Arquivo VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Adicionar os namespaces exigidos para o `CommandTable` elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  No `CommandTable` elemento, adicionar um `Commands` elemento para hospedar todos seus menus personalizados, as barras de ferramentas, grupos de comando e comandos. Para que podem carregar os elementos de interface do usuário personalizados, o `Commands` elemento deve ter seu `Package` atributo definido como o nome do pacote.  
  
     Após o `Commands` elemento, adicionar um `Symbols` elemento para definir os GUIDs para o pacote e os nomes e IDs de comando para elementos de interface do usuário.  
  
### <a name="including-visual-studio-resources"></a>Incluindo recursos do Visual Studio  
 Use o [Extern](../../extensibility/extern-element.md) elemento para acessar os arquivos que definem os comandos do Visual Studio e os menus que são necessárias para colocar os elementos da interface do usuário no IDE. Se você usar comandos definidos fora do seu pacote, use o [UsedCommands](../../extensibility/usedcommands-element.md) elemento para informar o Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Para incluir recursos do Visual Studio  
  
1.  Na parte superior do `CommandTable` elemento, adicione uma `Extern` elemento para cada arquivo externo ser referenciado e definir o `href` de atributo para o nome do arquivo. Você pode referenciar os seguintes arquivos de cabeçalho para acessar os recursos do Visual Studio:  
  
    -   Stdidcmd.h, define as IDs de todos os comandos expostos pelo Visual Studio.  
  
    -   Vsshlids.h, contém as IDs de comando para os menus do Visual Studio.  
  
2.  Se o seu pacote chama os comandos que são definidos pelo Visual Studio ou por outros pacotes, adicione um `UsedCommands` elemento após o `Commands` elemento. Preencher este elemento com um [UsedCommand](../../extensibility/usedcommand-element.md) elemento para cada comando que é chamar não faz parte do seu pacote. Definir o `guid` e `id` atributos do `UsedCommand` elementos para os valores GUID e ID de comandos para chamar. Para obter mais informações sobre como localizar os comandos GUIDs e IDs do Visual Studio, consulte [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para chamar comandos de outros pacotes, use o GUID e a ID do comando conforme definido no arquivo. VSCT para esses pacotes.  
  
### <a name="declaring-ui-elements"></a>Declarando elementos de interface do usuário  
 Declarar todos os novos elementos de interface do usuário no `Symbols` seção do arquivo. VSCT.  
  
##### <a name="to-declare-ui-elements"></a>Para declarar os elementos de interface do usuário  
  
1.  No `Symbols` elemento, adicionar três [GuidSymbol](../../extensibility/guidsymbol-element.md) elementos. Cada `GuidSymbol` elemento tem um `name` atributo e um `value` atributo. Definir o `name` para que ele reflita o objetivo do elemento de atributo. O `value` atributo tem um GUID. (Para gerar um GUID, o **ferramentas** menu, clique em **criar GUID**e, em seguida, selecione **formato do registro**.)  
  
     A primeira `GuidSymbol` elemento representa seu pacote e normalmente não tem filhos. O segundo `GuidSymbol` elemento representa o comando definido e contém todos os símbolos que definem a menus, grupos e comandos. O terceiro `GuidSymbol` elemento representa o repositório de imagens e contém símbolos para todos os ícones para seus comandos. Se você não tiver nenhum comando que usam ícones, você pode omitir o terceiro `GuidSymbol` elemento.  
  
2.  No `GuidSymbol` elemento que representa o conjunto de comandos, adicione um ou mais [IDSymbol](../../extensibility/idsymbol-element.md) elementos. Cada um deles representa um menu, barra de ferramentas, grupo ou comando que você está adicionando à interface do usuário.  
  
     Para cada `IDSymbol` elemento, defina o `name` de atributo para o nome que você usará para se referir ao menu correspondente, do grupo ou do comando e, em seguida, defina o `value` elemento em um número hexadecimal que representa sua id de comando. Não há dois `IDSymbol` elementos que têm o mesmo pai podem ter o mesmo valor.  
  
3.  Se qualquer um de seus elementos de interface do usuário exigem ícones, adicione um `IDSymbol` elemento para cada ícone para o `GuidSymbol` elemento que representa o repositório de imagens.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Colocar os elementos de interface do usuário no IDE  
 O [Menus](../../extensibility/menus-element.md) elemento [grupos](../../extensibility/groups-element.md) elemento, e [botões](../../extensibility/buttons-element.md) elemento contêm as definições de todos os grupos, menus e comandos que são definidos no pacote. Coloque esses comandos, menus e grupos no IDE usando um [pai](../../extensibility/parent-element.md) elemento, que faz parte da definição de elemento de interface do usuário, ou usando um [CommandPlacement](../../extensibility/commandplacement-element.md) elemento que é definido em outro lugar.  
  
 Cada `Menu`, `Group`, e `Button` elemento tem um `guid` atributo e um `id` atributo. Sempre definido o `guid` atributo para corresponder ao nome do `GuidSymbol` elemento que representa o comando definido e defina o `id` de atributo para o nome do `IDSymbol` elemento que representa o menu, grupo ou comando de `Symbols`seção.  
  
##### <a name="to-define-ui-elements"></a>Para definir os elementos de interface do usuário  
  
1.  Se você estiver definindo quaisquer novos menus, submenus, menus de atalho ou barras de ferramentas, adicione um `Menus` elemento para o `Commands` elemento. Em seguida, para cada menu a ser criado, adicione uma [Menu](../../extensibility/menu-element.md) elemento para o `Menus` elemento.  
  
     Definir o `guid` e `id` atributos do `Menu` elemento e defina o `type` de atributo para o tipo de menu que você deseja. Você também pode definir o `priority` atributo para estabelecer a posição relativa do menu do grupo pai.  
  
    > [!NOTE]
    >  O `priority` atributo não se aplica a barras de ferramentas e menus de contexto.  
  
2.  Todos os comandos no IDE do Visual Studio devem ser hospedados por grupos de comando, que são filhos diretos de menus e barras de ferramentas. Se você estiver adicionando novos menus ou barras de ferramentas para o IDE, eles devem conter novos grupos de comando. Você também pode adicionar grupos de comando existente menus e barras de ferramentas, você pode agrupar visualmente seus comandos.  
  
     Quando você adicionar novos grupos de comando, você deve primeiro criar um `Groups` elemento e, em seguida, adicione a ele um [grupo](../../extensibility/group-element.md) elemento para cada grupo de comando.  
  
     Definir o `guid` e `id` atributos de cada `Group` elemento e defina o `priority` atributo para estabelecer a posição relativa do grupo no menu pai. Para obter mais informações, consulte [criando grupos reutilizável de botões](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Se você estiver adicionando novos comandos ao IDE, adicione um `Buttons` elemento para o `Commands` elemento. Em seguida, para cada comando, adicione um [botão](../../extensibility/button-element.md) elemento para o `Buttons` elemento.  
  
    1.  Definir o `guid` e `id` atributos de cada `Button` elemento e defina o `type` de atributo para o tipo de botão desejado. Você também pode definir o `priority` atributo para estabelecer a posição relativa do comando no grupo pai.  
  
        > [!NOTE]
        >  Use `type="button"` para botões das barras de ferramentas e comandos de menu padrão.  
  
    2.  No `Button` elemento, adicionar um [cadeias de caracteres](../../extensibility/strings-element.md) elemento que contém um [ButtonText](../../extensibility/buttontext-element.md) elemento e um [CommandName](../../extensibility/commandname-element.md) elemento. O `ButtonText` elemento fornece o rótulo de texto para um item de menu ou a dica de ferramenta para um botão de barra de ferramentas. O `CommandName` elemento fornece o nome do comando para usar o comando também.  
  
    3.  Se o comando terá um ícone, crie um [ícone](../../extensibility/icon-element.md) elemento o `Button` elemento e defina seu `guid` e `id` atributos para o `Bitmap` elemento para o ícone.  
  
        > [!NOTE]
        >  Botões da barra de ferramentas devem ter ícones.  
  
     Para obter mais informações, consulte [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Se algum dos seus comandos exigir ícones, adicione um [Bitmaps](../../extensibility/bitmaps-element.md) elemento para o `Commands` elemento. Em seguida, para cada ícone, adicione um [Bitmap](../../extensibility/bitmap-element.md) elemento para o `Bitmaps` elemento. Isso é onde você pode especificar o local do recurso de bitmap. Para obter mais informações, consulte [adicionando ícones para comandos de Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Você pode confiar na estrutura paternidade colocar corretamente a maioria dos menus, grupos e comandos. Para conjuntos de comandos muito grandes, ou quando um menu, o grupo ou o comando deve aparecer em vários locais, é recomendável que você especifique o posicionamento de comando.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Confiar em paternidade para colocar elementos de interface do usuário no IDE  
  
1.  Para paternidade típica, crie um `Parent` elemento em cada `Menu`, `Group`, e `Command` elemento que é definido no pacote.  
  
     O destino do `Parent` elemento é o grupo que contém o menu ou menu, grupo ou comando.  
  
    1.  Definir o `guid` de atributo para o nome do `GuidSymbol` elemento que define o conjunto de comandos. Se o elemento de destino não faz parte do pacote, use o guid para esse conjunto de comandos, conforme definido no arquivo. VSCT correspondente.  
  
    2.  Definir o `id` atributo para corresponder a `id` atributo do menu de destino ou grupo. Para obter uma lista dos menus e grupos que são expostos pelo Visual Studio, consulte [GUIDs e IDs do Visual Studio Menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs e IDs do Visual Studio barras de ferramentas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Se você tiver um grande número de elementos de interface do usuário para colocar no IDE, ou se você tiver elementos que devem aparecer em vários locais, defina suas posições no [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, conforme mostrado nas etapas a seguir.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar o posicionamento de comando para colocar elementos de interface do usuário no IDE  
  
1.  Após o `Commands` elemento, adicionar um `CommandPlacements` elemento.  
  
2.  No `CommandPlacements` elemento, adicionar um `CommandPlacement` elemento para cada menu, um grupo ou um comando para colocar.  
  
     Cada `CommandPlacement` elemento ou `Parent` elemento coloca um menu, grupo ou comando em um local do IDE. Um elemento de interface do usuário só pode ter um pai, mas ele pode ter vários posicionamentos de comando. Para colocar um elemento de interface do usuário em vários locais, adicione um `CommandPlacement` elemento para cada local.  
  
3.  Definir o `guid` e `id` atributos de cada `CommandPlacement` elemento para o menu de hospedagem ou grupo, exatamente como você faria para uma `Parent` elemento. Você também pode definir o `priority` atributo para estabelecer a posição relativa do elemento de interface do usuário.  
  
 Você pode misturar posicionamento por paternidade e o posicionamento de comando. No entanto, para conjuntos de comandos muito grandes, recomendamos que você use somente o posicionamento de comando.  
  
### <a name="adding-specialized-behaviors"></a>Adicionando comportamentos especializados  
 Você pode usar [CommandFlag](../../extensibility/command-flag-element.md) para modificar o comportamento de menus e comandos, por exemplo, para alterar sua aparência e a visibilidade de elementos. Você também pode afetar quando um comando é visível usando [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), ou adicionar atalhos de teclado usando [associações](../../extensibility/keybindings-element.md). Determinados tipos de menus e comandos de já tem especializado comportamentos internos.  
  
##### <a name="to-add-specialized-behaviors"></a>Para adicionar comportamentos especializados  
  
1.  Para tornar um elemento de interface do usuário visível apenas em determinados contextos de interface do usuário, por exemplo, quando uma solução é carregada, use restrições de visibilidade.  
  
    1.  Após o `Commands` elemento, adicionar um `VisibilityConstraints` elemento.  
  
    2.  Para cada item de interface do usuário restringir, adicione um [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Para cada `VisibilityItem` elemento, defina o `guid` e `id` atributos no menu, grupo, ou comando e, em seguida, defina o `context` de atributo para o contexto de interface do usuário desejado, conforme definido no <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe. Para obter mais informações, consulte [VisibilityItem elemento](../../extensibility/visibilityitem-element.md).  
  
2.  Para definir a visibilidade ou a disponibilidade de um item de interface do usuário no código, use um ou mais dos seguintes sinalizadores de comando:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Para obter mais informações, consulte [comando sinalizador elemento](../../extensibility/command-flag-element.md).  
  
3.  Para alterar como um elemento é exibido ou alterar sua aparência dinamicamente, use um ou mais dos seguintes sinalizadores de comando:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextoAltera  
  
    -   TextOnly  
  
     Para obter mais informações, consulte [comando sinalizador elemento](../../extensibility/command-flag-element.md).  
  
4.  Para alterar como um elemento reage quando ele recebe comandos, use um ou mais dos seguintes sinalizadores de comando:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Teclas de filtragem  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Para obter mais informações, consulte [comando sinalizador elemento](../../extensibility/command-flag-element.md).  
  
5.  Para anexar um atalho de teclado dependente de menu a um menu ou um item em um menu, adicionar um caractere e comercial ('& ') no `ButtonText` elemento para o item de menu ou menu. O caractere que segue o e comercial é o atalho de teclado ativa quando o menu pai estiver aberto.  
  
6.  Para anexar um atalho de teclado do menu independente para um comando, use [associações](../../extensibility/keybindings-element.md). Para obter mais informações, consulte [KeyBinding elemento](../../extensibility/keybinding-element.md).  
  
7.  Para localizar o texto do menu, use o `LocCanonicalName` elemento. Para obter mais informações, consulte [elemento cadeias de caracteres](../../extensibility/strings-element.md).  
  
 Alguns tipos de menu e o botão incluem comportamentos especializados. A tabela a seguir descreve algumas menu especializada e tipos de botão. Para outros tipos, consulte o `types` atributo descrições em [elemento Menu](../../extensibility/menu-element.md), [elemento Button](../../extensibility/button-element.md), e [combinação elemento](../../extensibility/combo-element.md).  
  
 Caixa de combinação  
 Uma caixa de combinação é uma lista suspensa que pode ser usada em uma barra de ferramentas. Para adicionar caixas de combinação para a interface do usuário, crie um [combinações](../../extensibility/combos-element.md) elemento o `Commands` elemento. Em seguida, adicione ao `Combos` elemento um `Combo` elemento para cada caixa de combinação adicionar. `Combo`elementos têm os mesmos atributos e filhos como `Button` elementos e também ter `DefaultWidth` e `idCommandList` atributos. O `DefaultWidth` atributo define a largura em pixels e o `idCommandList` pontos de atributo a uma ID de comando que é usada para popular a caixa de combinação. Para obter mais informações, consulte o `Combo` documentação do elemento.  
  
 MenuController  
 Um controlador de menu é um botão com uma seta ao lado dele. Clique na seta abre uma lista. Para adicionar um controlador de menu para a interface do usuário, crie um `Menu` elemento e defina seu `type` atributo **MenuController** ou **MenuControllerLatched**, dependendo do comportamento desejado. Para popular um controlador de menu, defina-o como o pai de um `Group` elemento. O controlador de menu exibirá todos os filhos desse grupo na lista suspensa.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos e Menus estendendo](../../extensibility/extending-menus-and-commands.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)