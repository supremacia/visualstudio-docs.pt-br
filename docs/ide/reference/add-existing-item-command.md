---
title: Comando Adicionar Item Existente | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a94546b8e480a661c175f946cc376fa92b30cbf8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="add-existing-item-command"></a>Comando Adicionar Item Existente
Adiciona um arquivo existente à solução atual e abre-o.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Necessário. O caminho completo e o nome do arquivo, com a extensão, do item a adicionar à solução atual. Se o caminho do arquivo ou o nome do arquivo contiver espaços, coloque todo o caminho entre aspas.  
  
## <a name="switches"></a>Opções  
 /e: `editorname`  
 Opcional. Nome do editor no qual o arquivo será aberto. Se o argumento for especificado, mas nenhum nome de editor for fornecido, a caixa de diálogo **Abrir com** será exibida.  
  
 A sintaxe do argumento /e:`editorname` usa os nomes de editor como eles são exibidos na **Caixa de diálogo Abrir Com**, entre aspas. Por exemplo, para abrir uma folha de estilos no editor de código-fonte, insira o seguinte para o argumento /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Comentários  
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.  
  
## <a name="example"></a>Exemplo  
 Este exemplo adiciona o arquivo, Form1.frm, à solução atual.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)