---
title: Atividades de fluxo de trabalho herdado | Microsoft Docs
ms.date: 01/18/2017
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 61c719725f3d4ebfffe291ff31115ddd0cc5f3d4
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="legacy-workflow-activities"></a>Atividades herdados de fluxo de trabalho

[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] inclui um conjunto padrão de atividades que fornecem a funcionalidade para o fluxo de controle, as condições, manipulação de eventos, o gerenciamento de estado, e a comunicação com aplicativos e serviços. Durante a criação de fluxos de trabalho, você pode usar as atividades fornecidas pelo sistema que são fornecidas pelo Designer de fluxo de trabalho do Windows, ou você pode criar suas próprias atividades personalizadas.

 A tabela a seguir lista o conjunto de atividade de para fora da estrutura de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] . Muitas, mas não todas, essas atividades são representados pelos designers de atividade que podem ser acessados a partir de **caixa de ferramentas** do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Para criar uma atividade, arraste seu designer do **caixa de ferramentas** e solte-o na superfície de design.

|Atividade|Descrição|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Usado com o **HandleExternalEventActivity** atividade para comunicações de entrada e saídas com um serviço local. Para obter mais informações, consulte [usando a atividade CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Usado para conter a lógica de limpeza para uma atividade composta cancelada antes de filhos de quaisquer atividades composto é executar concluído. Para obter mais informações, consulte [usando a atividade CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Permite que você adicione Visual Basic ou código em c ao fluxo de trabalho. Para obter mais informações, consulte [usando a atividade de CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Uma versão compensatable de <xref:System.Workflow.Activities.SequenceActivity>. Para obter mais informações, consulte [usando a atividade de CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Uma versão compensável de **TransactionScopeActivity**. Para obter mais informações, consulte [usando a atividade de CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Permite que você chamar código para desfazer ou compensar operações já executadas pelo fluxo de trabalho quando ocorre um erro. Para obter mais informações, consulte [usando a atividade de CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Um wrapper para uma ou mais atividades que executam a compensação de uma atividade TransactionScopeActivity concluída para obter mais informações, consulte [usando a atividade CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Executa atividades filho com base em uma condição que se aplica a <xref:System.Workflow.Activities.ConditionedActivityGroup> atividade em si e com base nas condições que se aplicam separadamente para cada filho. Para obter mais informações, consulte [usando a atividade de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Permite que você crie os atrasos no fluxo de trabalho que são baseados em um intervalo de tempo limite. Para obter mais informações, consulte [usando a atividade DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Envolve uma ou mais atividades que são executadas quando ocorre um evento especificado. Para obter mais informações, consulte [usando a atividade de EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Fornece uma estrutura para associar eventos com uma atividade. Para obter mais informações, consulte [usando a atividade EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Executa sua atividade filho principal simultaneamente com um <xref:System.Workflow.Activities.EventHandlersActivity>. Para obter mais informações, consulte [usando a atividade EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Usado para manipular uma exceção de um tipo que você especificar. Para obter mais informações, consulte [usando a atividade FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Representa uma atividade composta que tem uma lista ordenada de atividades filho do tipo **System.Workflow.Activities.FaultHandlerActivity**. Para obter mais informações, consulte [usando a atividade FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Usado em conjunto com o <xref:System.Workflow.Activities.CallExternalMethodActivity> atividade para comunicações de entrada e saídas com um serviço local. Para obter mais informações, consulte [usando a atividade HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Testa uma condição em cada ramificação e executa as atividades na primeira ramificação para a qual a condição é igual a **true**. Para obter mais informações, consulte [usando a atividade IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Representa uma ramificação de um <xref:System.Workflow.Activities.IfElseActivity>. Para obter mais informações, consulte [usando a atividade de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Permite que seu fluxo de trabalho para chamar um serviço Web. Para obter mais informações, consulte [usando a atividade de InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Permite que seu fluxo de trabalho para chamar outro fluxo de trabalho. Para obter mais informações, consulte [usando a atividade de InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Uma atividade composta que contém apenas <xref:System.Workflow.Activities.EventDrivenActivity> atividades filho. Para obter mais informações, consulte [usando a atividade ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Fornece uma maneira de agendar dois ou mais filhos **SequenceActivity** ramificações da atividade de processamento ao mesmo tempo. Para obter mais informações, consulte [usando a atividade de ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|Uso representar um conjunto de regras. Uma regra consiste em circunstâncias e em ações resultantes. Para obter mais informações, consulte [usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Cria várias instâncias de uma única atividade filho. Para obter mais informações, consulte [usando a atividade ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Fornece uma maneira simples de vincular várias juntos para atividades a execução sequencial. Para obter mais informações, consulte [usando a atividade SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Especifica uma transição para um novo estado. Para obter mais informações, consulte [usando a atividade de SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Representa um estado em um fluxo de trabalho do computador de estado. Para obter mais informações, consulte [usando a atividade de StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Usado em uma <xref:System.Workflow.Activities.StateActivity> atividade como um contêiner para as atividades filho que são executadas ao sair do **StateActivity** atividade. Para obter mais informações, consulte [usando a atividade de StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Usado em uma <xref:System.Workflow.Activities.StateActivity> atividade como um contêiner para as atividades filho que são executadas quando inserir o **StateActivity** atividade. Para obter mais informações, consulte [usando a atividade de StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Suspende a operação de seu fluxo de trabalho para ativar a intervenção no caso de alguma condição de erro que requer a atenção especial. Para obter mais informações, consulte [usando a atividade de SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Executa sequencialmente atividades contidas em um domínio sincronizado. Para obter mais informações, consulte [usando a atividade de SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Permite que você terminar imediatamente a operação de seu fluxo de trabalho no caso de uma condição de erro. Para obter mais informações, consulte [usando a atividade de TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Permite que você capturar exceções lançadas corporativos como parte de metadados do processo para um fluxo de trabalho. Para obter mais informações, consulte [usando a atividade de ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Fornece uma estrutura para transações e manipulação de exceção. Para obter mais informações, consulte [usando a atividade TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Permite que você a modelagem a ocorrência de uma falha de serviço Web. Para obter mais informações, consulte [usando a atividade de WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Receber dados de um serviço Web. Para obter mais informações, consulte [usando a atividade de WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Responde a uma solicitação de serviço Web feita a um fluxo de trabalho. Para obter mais informações, consulte [usando a atividade de WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Permite que seu fluxo de trabalho para executar um loop até que uma condição seja satisfeita. Para obter mais informações, consulte [usando a atividade WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

 Para obter mais informações sobre como criar atividades personalizadas, consulte [o desenvolvimento de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65023) e [usando o Designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>Consulte também

- [Atividades do Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)
- [Fluxos de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65010)
- [Desenvolvimento de atividades de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65023)