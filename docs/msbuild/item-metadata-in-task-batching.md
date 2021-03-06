---
title: Metadados de itens no envio de tarefas em lote | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ee203056edb24bd2338caf1ad1b5608e4c5d3ca9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="item-metadata-in-task-batching"></a>Metadados de itens na separação de tarefas em lotes
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tem a capacidade de dividir as listas de itens em diferentes categorias ou lotes, com base nos metadados do item, além de executar uma tarefa uma única vez com cada lote. Pode ser difícil entender exatamente quais itens estão sendo passados com qual lote. Este tópico aborda os cenários comuns a seguir, que envolvem o envio em lote.  
  
-   Divisão de uma lista de itens em lotes  
  
-   Divisão de várias listas de itens em lotes  
  
-   Envio em lote, um item por vez  
  
-   Filtragem de listas de itens  
  
 Para obter mais informações sobre envio em lote com [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consulte [Envio em lote](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Divisão de uma lista de itens em lotes  
 O envio em lote permite que você divida uma lista de itens em lotes diferentes com base nos metadados do item e passe cada um dos lotes em uma tarefa separadamente. Isso é útil para a criação de assemblies satélite.  
  
 O exemplo a seguir mostra como dividir uma lista de itens em lotes com base nos metadados do item. A lista de itens `ExampColl` é dividida em três lotes com base nos metadados do item `Number`. A presença de `%(ExampColl.Number)` no atributo `Text` notifica o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de que o envio em lote deve ser realizado. A lista de itens `ExampColl` é dividida em três lotes com base nos metadados `Number` e cada lote é passado separadamente para a tarefa.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 A [Tarefa Message](../msbuild/message-task.md) exibe as seguintes informações:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Divisão de várias listas de itens em lotes  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pode dividir várias listas de itens em lotes com base nos mesmos metadados. Isso facilita a divisão listas de itens diferentes em lotes para criar vários assemblies. Por exemplo, você poderia ter uma lista de itens de arquivos .cs divididos em um lote de aplicativo e um lote de assembly e uma lista de itens de arquivos de recurso divididos em um lote de aplicativo e um lote de assembly. Você poderia então usar o envio em lote para passar essas listas de itens em uma tarefa e compilar ambos o aplicativo e o assembly.  
  
> [!NOTE]
>  Se uma lista de itens sendo passada em uma tarefa não contiver itens com os metadados referenciados, cada item nessa lista será passado para todos os lotes.  
  
 O exemplo a seguir mostra como dividir uma lista com vários itens em lotes com base nos metadados do item. Cada uma das listas de itens `ExampColl` e `ExampColl2` é dividida em três lotes com base nos metadados do item `Number`. A presença de `%(Number)` no atributo `Text` notifica o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de que o envio em lote deve ser realizado. As listas de itens `ExampColl` e `ExampColl2` são divididas em três lotes com base nos metadados `Number` e cada lote é passado separadamente para a tarefa.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 A [Tarefa Message](../msbuild/message-task.md) exibe as seguintes informações:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Envio em lote, um item por vez  
 O envio em lote também pode ser executado nos metadados de itens conhecidos que são atribuídos a cada item no momento da criação. Isso assegura que cada item em uma coleção tenha alguns metadados para usar para o envio em lote. O valor de metadados `Identity` é exclusivo para cada item e é útil para dividir cada item em uma lista de itens em um lote separado. Para obter uma lista completa dos metadados de itens conhecidos, consulte [Metadados de itens conhecidos](../msbuild/msbuild-well-known-item-metadata.md).  
  
 O exemplo a seguir mostra como enviar em lote cada item em uma lista de itens, um por vez. Já que o valor `Identity` dos metadados de cada item é exclusivo, a lista de itens `ExampColl` é dividida em seis lotes, cada lote contendo um item da lista de itens. A presença de `%(Identity)` no atributo `Text` notifica o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de que o envio em lote deve ser realizado.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 A [Tarefa Message](../msbuild/message-task.md) exibe as seguintes informações:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Filtragem de listas de itens  
 O envio em lote pode ser usado para filtrar certos itens de uma lista de itens antes de passá-la para uma tarefa. Por exemplo, filtrar o valor `Extension` de metadados de itens conhecidos permite que você execute uma tarefa somente em arquivos com uma extensão específica.  
  
 O exemplo a seguir mostra como dividir uma lista de itens em lotes com base nos metadados de item e, em seguida, filtrar esses lotes quando eles são passados para uma tarefa. A lista de itens `ExampColl` é dividida em três lotes com base nos metadados do item `Number`. O atributo `Condition` da tarefa especifica que somente lotes com um valor `2` para os metadados de item `Number` serão passados para a tarefa  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 A [Tarefa Message](../msbuild/message-task.md) exibe as seguintes informações:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Consulte também  
 [Metadados de itens conhecidos](../msbuild/msbuild-well-known-item-metadata.md)   
 [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)