---
title: 'How to: Create a PolicyActivity Rule Set (Legacy) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: ErikRe
ms.author: erikre
manager: erikre
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 21a413a3e2d17d77fd83d5109587a96f323a0511
ms.openlocfilehash: 42d94d625e2ad7db23dbd4917107b8da4f24009b
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>How to: Create a PolicyActivity Rule Set (Legacy)
This topic describes how to create a policy activity rule set using the legacy [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] that targets the [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] or the [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 After you have dragged a **Policy** activity item from the **Toolbox** to the workflow design surface, you will want to select an existing rule or create a new rule set for the [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) activity. You select an existing rule set by using the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) and you create rule sets by using the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  You can open the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) dialog box directly by double-clicking on a [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) activity that is on the workflow design surface.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>To select or create a rule set for a PolicyActivity activity  
  
1.  Right-click the [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), and then click **Properties** to open the **Properties** window.  
  
2.  Click the **RuleSetReference** property.  
  
3.  Do one of the following:  
  
    -   Click the **RuleSetReference** ellipsis **[...]**, and then select an existing rule set in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Then go to step 10.  
  
         -or-  
  
    -   Type a name for a rule set. Click the **RuleSetReference** ellipsis **[...]**, and then select **Edit** in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         -or-  
  
    -   Type a name for a rule set. Expand the **RuleSetReference** property and select the ellipsis **[...]** in the **RuleSet Definition** property.  
  
         The [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) opens.  
  
4.  In the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), click **Add Rule** to add a new rule to the rule set.  
  
5.  Enter the **Name**, **Priority**, and **Reevaluation** properties, or keep the default values.  
  
6.  Enter the text for the **Condition**.  
  
7.  Enter the text for the **Then Actions** and the **Else Actions**.  
  
8.  Click **Add Rule** again to add another rule.  
  
9. When you are finished, click **OK**.  
  
## <a name="see-also"></a>See Also  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Using the Policy Activity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)