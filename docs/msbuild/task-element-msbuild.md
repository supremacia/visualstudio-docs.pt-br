---
title: Elemento Task (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
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
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9b2829c09d22abe37a2f7718b0016db73d9539d6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="task-element-msbuild"></a>Elemento Task (MSBuild)
Cria e executa uma instância de uma tarefa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. O nome do elemento é determinado pelo nome da tarefa que está sendo criada.  

 \<Project>  
 \<Target>  

## <a name="syntax"></a>Sintaxe  

```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Condition`|Atributo opcional. Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Atributo opcional. Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true**. Quando uma tarefa falha, as tarefas subsequentes no elemento de [Destino](../msbuild/target-element-msbuild.md) e o build continuam em execução e todos os erros da tarefa são tratados como avisos.<br />-   **ErrorAndContinue**. Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento de `Target` e o build são considerados como em falha.<br /><br /> As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.<br /><br /> Para obter mais informações, consulte [Como Ignorar Erros em Tarefas](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Será necessário se a classe de tarefa contiver uma ou mais propriedades rotuladas com o atributo `[Required]`.<br /><br /> Um parâmetro de tarefa definido pelo usuário que contém o valor do parâmetro como seu valor. Pode haver qualquer quantidade de parâmetros no elemento `Task`, com cada atributo mapeado para uma propriedade do .NET na classe tarefa.|  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Saída](../msbuild/output-element-msbuild.md)|Armazena saídas da tarefa no arquivo de projeto. Pode haver zero ou mais elementos `Output` em uma tarefa.|  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Elemento contêiner para tarefas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Comentários  
 Um elemento `Task` em um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] cria uma instância de uma tarefa, define suas propriedades e a executa. O elemento `Output` armazena parâmetros de saída em propriedades ou itens para serem usados em outro local do arquivo de projeto.  

 Se houver elementos [OnError](../msbuild/onerror-element-msbuild.md) no elemento pai `Target` de uma tarefa, eles ainda serão avaliados se a tarefa falhar e `ContinueOnError` tiver o valor de `false`. Para obter mais informações sobre tarefas, consulte [Tarefas](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria uma instância da classe [tarefa Csc](../msbuild/csc-task.md), define seis propriedades e executa a tarefa. Após a execução, o valor da propriedade `OutputAssembly` do objeto é colocada em uma lista de itens com o nome `FinalAssemblyName`.  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
