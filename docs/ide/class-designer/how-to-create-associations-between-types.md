---
title: "Como criar associações entre tipos (Designer de Classe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa4c994ffadf04c3205762d0018d18ad14ffd6c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Como criar associações entre tipos (Designer de Classe)
As linhas de associação no Designer de Classe mostram como as classes em um diagrama são relacionadas. Uma linha de associação representa uma classe que é o tipo de uma propriedade ou de um campo de outra classe no seu projeto. As linhas de associação geralmente são usadas para ilustrar as relações mais importantes entre classes do projeto.  
  
Embora você possa exibir todos os campos e propriedades como associações, faz mais sentido mostrar apenas membros importantes como associações, dependendo do que você pretende enfatizar no diagrama. (É possível mostrar membros menos importantes como membros regulares ou ocultá-los no geral.)  
  
> [!NOTE]
>  O Designer de Classe oferece suporte apenas a associações unidirecionais.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Para definir uma linha de associação no Diagrama de Classes  
  
1.  Na Caixa de Ferramentas, em Designer de Classe, selecione **Associação**.  
  
2.  Desenhe uma linha entre as duas formas que deseja vincular a uma associação.  
  
     Uma nova propriedade é criada na primeira classe. Essa propriedade é exibida como uma linha de associação (não como uma propriedade em um compartimento na forma) com um nome padrão. Seu tipo é a forma para a qual a linha de associação aponta.
  
### <a name="to-change-the-name-of-an-association"></a>Para alterar o nome de uma associação  
  
-   Na superfície de diagrama, clique no rótulo da linha de associação e edite-o.  
  
 \- ou -  
  
1.  Clique na forma que contém a propriedade que é mostrada como uma associação.  
  
     A forma obtém foco e seus membros são exibidos na janela Detalhes da Classe e na janela Propriedades.  
  
2.  Na janela Detalhes da Classe ou na janela Propriedades, edite o campo de nome da propriedade e pressione Enter.  
  
     O nome é atualizado na Janela **Detalhes da Classe**, na linha de associação, na janela Propriedades e no código.  
  
## <a name="see-also"></a>Consulte também
[Como alternar entre notação de membro e de associação](how-to-change-between-member-notation-and-association-notation.md)