---
title: Tarefa CreateVisualBasicManifestResourceName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 133b1b6cf881d014c93391b316710975a84a2f21
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Tarefa CreateVisualBasicManifestResourceName
Cria um nome de manifesto de estilo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] de um nome de arquivo .resx fornecido ou de outro recurso.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da [tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ManifestResourceNames`|Parâmetro de saída somente leitura <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Os nomes de manifesto resultantes.|  
|`ResourceFiles`|Parâmetro `String` obrigatório.<br /><br /> O nome do arquivo de recurso do qual criar o nome do manifesto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`RootNamespace`|Parâmetro `String` opcional.<br /><br /> O namespace raiz do arquivo de recurso, geralmente obtido do arquivo de projeto. Pode ser `null`.|  
|`PrependCultureAsDirectory`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o nome da cultura é adicionado como um nome de diretório antes do nome do recurso de manifesto. O valor padrão é `true`.|  
|`ResourceFilesWithManifestResourceNames`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o nome do arquivo de recurso que agora inclui o nome do recurso de manifesto.|  
  
## <a name="remarks"></a>Comentários  
 A [tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina o nome do recurso de manifesto apropriado para atribuir a um determinado arquivo .resx ou outro arquivo de recurso. A tarefa fornece um nome lógico para um arquivo de recurso e, em seguida, anexa-o a um parâmetro de saída como metadados.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)