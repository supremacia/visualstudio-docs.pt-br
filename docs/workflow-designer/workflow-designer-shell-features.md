---
title: Recursos do Shell do Designer de fluxo de trabalho | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 21fa46d9d70ad69f4d3e0ccfc55f85ade331feb4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="workflow-designer-shell-features"></a>funcionalidades de Designer de Fluxo de Trabalho Shell

Designer de fluxo de trabalho do Windows é composto por três áreas da interface do usuário principais: a superfície do designer, a barra de navegação estrutural acima dele e o shell abaixo dela. A barra de rastreamento, posicionado na parte superior da tela, é usada para exibir a lista de ancestrais de atividade da raiz atual. Para obter mais informações, consulte [como: Use navegação](../workflow-designer/how-to-use-breadcrumb-navigation.md). A superfície de designer, posicionado no centro da tela, é usada para compondo fluxos de trabalho. O shell, localizado na parte inferior da tela, contém um número de botões para gerenciar o modo de exibição atual.

## <a name="shell-features"></a>Recursos de Shell
 O shell tem botões no lado direito da barra que você pode usar para ampliar ou do fluxo de trabalho, para caber o conteúdo do fluxo de trabalho o tamanho da tela, e de apresentação ou para ocultar o mapa da revisão. Você também pode ampliar ou fora de um fluxo de trabalho usando os atalhos de teclado CTRL++ e CTRL+-.

## <a name="overview-map"></a>Visão geral de mapa
 O mapa da visão geral exibe uma pequena versão da atividade inteira na raiz atual de rastreamento, incluindo todos seus filhos e todos os seus filhos expandidos. Há um viewport, um retângulo com uma borda laranja, que realça a parte da atividade exibida atualmente dentro do editor. Arraste o retângulo em torno do mapa da visão geral rola o designer de fluxo de trabalho e altera a exibição do editor.

> [!NOTE]
> A interface do usuário de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] é virtualizada. Os designers de atividade são processados somente se necessário. Se uma parte do fluxo de trabalho foi desenhada nunca na superfície do designer, essa parte aparece como o branco no mapa da revisão. Rolagem em torno do mapa da visão geral desenha completamente o fluxo de trabalho.

## <a name="copying-or-saving-workflows-as-images"></a>Copiando ou salvando fluxos de trabalho como imagens
 Fluxos de trabalho podem ser copiados no formato de bitmap ou ser salvos no formato de bitmap ou vetorial. Copiar ou salvar uma imagem fornecem uma maneira para exportar um modo de exibição da atividade inteira na raiz atual de rastreamento, incluindo todos seus filhos e todos os seus filhos expandidos a outros programa.

 Para copiar como imagem, clique em qualquer lugar no designer e selecione **cópia como imagem**. Para salvar como imagem, clique em qualquer lugar no designer e selecione **Salvar como imagem**. Fluxos de trabalho podem ser salvos no formato de JPG, PNG, GIF, ou XPS. O formato é selecionado no **Salvar como** da caixa de diálogo de **Salvar como tipo:** suspensa da caixa de listagem na parte inferior da janela.

## <a name="fonts-and-colors"></a>Fontes e cores

As fontes usadas em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dentro de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] são controladas pela fonte de ambiente. As cores exibidas em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] alterações se você estiver usando um esquema de cores de alto contraste para o tema do sistema operacional. Você deve reiniciar [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] depois de fazer uma alteração na fonte ou cor configurações antes que as alterações tenham efeito em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].