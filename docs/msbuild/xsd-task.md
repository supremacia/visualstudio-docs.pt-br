---
title: Tarefa XSD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d0324b3e72cfffb73e22b3995cfc9458631e7d5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="xsd-task"></a>Tarefa XSD
Encapsula a ferramenta de definição de esquema XML (xsd.exe), a qual gera arquivos de classe ou de esquema com base em uma origem.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **XSD**.  
  
-   **AdditionalOptions**  
  
     Parâmetro **String** opcional.  
  
     Uma lista de opções, conforme especificado na linha de comando. Por exemplo, "*/option1 /option2 /option#*". Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XSD**.  
  
-   **GenerateFromSchema**  
  
     Parâmetro **String** opcional.  
  
     Especifica os tipos gerados com base no esquema especificado.  
  
     Especifique um dos valores a seguir, cada um dos quais correspondente a uma opção XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Linguagem**  
  
     Parâmetro **String** opcional.  
  
     Especifica a linguagem de programação a ser usada para o código gerado.  
  
     Escolha **CS** (C#, que é o padrão), **VB** (Visual Basic) ou **JS** (JScript). Você também pode especificar um nome totalmente qualificado para uma classe que implementa `System.CodeDom.Compiler.CodeDomProvider Class`  
  
-   **Namespace**  
  
     Parâmetro **String** opcional.  
  
     Especifica o namespace de tempo de execução para os tipos gerados.  
  
-   **Sources**  
  
     Parâmetro `ITaskItem[]` obrigatório.  
  
     Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.  
  
-   **SuppressStartupBanner**  
  
     Parâmetro **Boolean** opcional.  
  
     Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.  
  
-   **TrackerLogDirectory**  
  
     Parâmetro **String** opcional.  
  
     Especifica o diretório do log de rastreamento.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)