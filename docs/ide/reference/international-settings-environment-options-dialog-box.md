---
title: "Caixa de diálogo Configurações Internacionais, Ambiente, Opções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e086111be924d1262866f882b77d821659af909d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="international-settings-environment-options-dialog-box"></a>Caixa de diálogo Configurações Internacionais, Ambiente, Opções
A página Configurações Internacionais permite alterar o idioma padrão quando você tem mais de uma versão de idioma do IDE (ambiente de desenvolvimento integrado) instalada em seu computador. Você pode acessar essa caixa de diálogo selecionando **Opções** no menu **Ferramentas** e, em seguida, escolhendo **Configurações Internacionais** na pasta **Ambiente**. Se essa página não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.  
  
> [!NOTE]
>  As opções disponíveis nas caixas de diálogo e os nomes os locais dos comandos de menu que você vê podem diferir do que é descrito na Ajuda, dependendo de suas configurações ativas ou da edição. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Linguagem**  
 Lista os idiomas disponíveis para as versões de idioma do produto instalado. Essa opção ficará não disponível a menos que você tenha mais de uma versão de idioma instalada no computador. Se vários idiomas de produtos ou uma instalação de idioma misto dos produtos compartilhar o ambiente, a seleção de idioma será alterada para **Usar o idioma do Microsoft Windows**.  
  
> [!CAUTION]
>  Em um sistema com vários idiomas instalados, as ferramentas de build do Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e arquivos relacionados) não são afetadas por essa configuração. Essas ferramentas usam a versão do último idioma instalado. As ferramentas de build do idioma instalado anteriormente são substituídas porque as ferramentas de build do Visual C++ não usam o modelo DLL satélite.  
  
## <a name="see-also"></a>Consulte também  
 [Instalar pacotes de idiomas](../../install/install-visual-studio.md#step-6---install-language-packs-optional)   
 [Caixa de diálogo Opções do Ambiente](../../ide/reference/environment-options-dialog-box.md)