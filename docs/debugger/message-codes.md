---
title: "Códigos de mensagem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 432012d897ecc4da508dd2925ac655b8dc9d1416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-codes"></a>Códigos de mensagem
Cada linha da mensagem mostrada [exibição de mensagens](../debugger/messages-view.md) contém 'P', do,' do,' ou 'R' código. Esses códigos têm os seguintes significados:  
  
|Código|Significado|  
|----------|-------------|  
|P|A mensagem foi postada para a fila com o **PostMessage** função. Nenhuma informação está disponível sobre a eliminação da mensagem.|  
|S|A mensagem foi enviada com o **SendMessage** função. Isso significa que o remetente não recuperar o controle até que o receptor processa e retorna a mensagem. O receptor, portanto, pode passar um valor de retorno para o remetente.|  
|s|A mensagem foi enviada, mas segurança impede o acesso para o valor de retorno.|  
|R|De cada ' linha tem uma linha correspondente de 'R' (retorno) que lista o valor de retorno da mensagem. Às vezes chamadas de mensagem são aninhadas, que significa que esse manipulador de uma mensagem envia outra mensagem.|