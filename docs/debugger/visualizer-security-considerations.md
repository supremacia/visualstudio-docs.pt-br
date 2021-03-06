---
title: "Considerações de segurança do Visualizador | Microsoft Docs"
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
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5075e55f1db35f7a588094a7c398c9d4c25483c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="visualizer-security-considerations"></a>Considerações de segurança do visualizador
Gravar um Visualizador envolve possíveis ameaças de segurança. Nenhuma exploração conhecida existe no momento para essas ameaças potenciais, mas os desenvolvedores devem estar atentos a elas e tomar as precauções apropriadas de segurança, conforme descrito aqui, para se proteger contra futuras explorações.  
  
 Os visualizadores do depurador exigem privilégios maiores do que são permitidos por um aplicativo de confiança parcial. Os visualizadores não serão carregados quando você for interrompido no código com confiança parcial. Para depurar usando um visualizador, você deverá executar o código com confiança total.  
  
## <a name="possible-malicious-debuggee-component"></a>Componente a ser depurado possivelmente mal-intencionado  
 Os visualizadores consistem em pelo menos duas classes: uma no lado do depurador e outra no lado a ser depurado. Os visualizadores são geralmente implantados em assemblies separados colocados em diretórios especiais, mas também podem ser carregados fora do lado a ser depurado. Quando isso ocorrer, o depurador retira o código do lado a ser depurado e executa-o dentro do depurador com confiança total.  
  
 Executar código do lado a ser depurado com confiança total torna-se problemático quando o lado a ser depurado não é totalmente confiável. Se um visualizador tentar carregar um assembly de confiança parcial do lado a ser depurado no depurador, o Visual Studio encerrará o visualizador.  
  
 No entanto, uma vulnerabilidade menor ainda existe. O lado a ser depurado pode associar-se a um lado do depurador que foi carregado de outra origem (não o lado a ser depurado). O lado a ser depurado pode dizer ao lado do depurador confiável para executar ações em seu nome. Se a classe do lado do depurador confiável expulsar um mecanismo de “excluir esse arquivo”, por exemplo, o lado a ser depurado de confiança parcial poderá invocar esse mecanismo quando o usuário invocar o visualizador.  
  
 Para atenuar essa vulnerabilidade, esteja atento às interfaces expostas pelo visualizador.  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura do Visualizador](../debugger/visualizer-architecture.md)   
 [Como: gravar um visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)