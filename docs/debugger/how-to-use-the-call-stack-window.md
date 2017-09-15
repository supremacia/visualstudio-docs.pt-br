---
title: View the call stack in the Visual Studio debugger | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
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
ms.sourcegitcommit: 9e6c28d42bec272c6fd6107b4baf0109ff29197e
ms.openlocfilehash: 83977d96d8e8503565f811608089279cfbef5d05
ms.contentlocale: pt-br
ms.lasthandoff: 08/22/2017

---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>View the call stack and use the Call Stack Window in the Visual Studio debugger

By using the **Call Stack** window, you can view the function or procedure calls that are currently on the stack. The **Call Stack** window shows the order in which methods and functions are getting called. The call stack is a good way to examine and understand the execution flow of an app.
  
When [debugging symbols](#bkmk_symbols) are not available for part of a call stack, the **Call Stack** window might not be able to display correct information for that part of the call stack. If that occurs, the following notation appears:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> The **Call Stack** window is similar to the Debug perspective in some IDEs like Eclipse. 

> [!NOTE]
>  The dialog boxes and menu commands you see might differ from those described here, depending on your active settings or edition. To change your settings, select **Import and Export Settings** on the **Tools** menu.  See [Personalizing the IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>View the call stack while in the debugger 
  
-   While debugging, in the **Debug** menu, select **Windows > Call Stack**.

 ![Call Stack Window](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

A yellow arrow identifies the stack frame where the execution pointer is currently located. By default, this is the stack frame whose information appears in the source, **Locals**, **Autos**, **Watch**, and **Disassembly** windows. If you want to change the debugger context to another frame on the stack, you can do that by [switching to another stack frame](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Display non-user code in the Call Stack window  
  
-   Right-click the **Call Stack** window and select **Show External Code**.

Non-user code is any code that is not shown when [Just My Code](../debugger/just-my-code.md) is enabled. In managed code, non-user code frames are hidden by default. The following notation appears instead of the non-user code frames:  
  
**[\<External Code>]**  
  
## <a name="bkmk_switch"></a> Switch to another stack frame (change the debugger context)
  
1.  In the **Call Stack** window, right-click the stack frame whose code and data that you want to view.

    Or, you can double-click a frame in the **Call Stack** window to switch to the selected frame. 
  
2.  Select **Switch to Frame**.  
  
     A green arrow with a curly tail appears next to the stack frame you selected. The execution pointer remains in the original frame, which is still marked with the yellow arrow. If you select **Step** or **Continue** from the **Debug** menu, execution will continue in the original frame, not the frame you selected.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>View the source code for a function on the call stack  
  
-   In the **Call Stack** window, right-click the function whose source code you want to see and select **Go To Source Code**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Run to a specific function from the Call Stack window  
  
-  In the **Call Stack** window, select the function, right-click and  choose **Run to Cursor**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Set a breakpoint on the exit point of a function call  
  
-   See [Set a breakpoint at a call stack function](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Display calls to or from another thread  
  
-   Right-click the **Call Stack** window and select **Include Calls To/From Other Threads**.   
  
## <a name="visually-trace-the-call-stack"></a>Visually trace the call stack  

If you are using Visual Studio Enterprise (only), you can view code maps for the call stack while debugging.

- In the **Call Stack** window, open the shortcut menu. Choose **Show Call Stack on Code Map**. (Keyboard: **CTRL** + **SHIFT** + **`**)  
  
    For detailed information, see [Map methods on the call stack while debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Show Call Stack on Code Map](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>View the disassembly code for a function on the call stack  
  
-   In the **Call Stack** window, right-click the function whose disassembly code you want to see and select **Go To Disassembly**.    

## <a name="change-the-optional-information-displayed"></a>Change the optional information displayed  
  
-   Right-click the **Call Stack** window and set or clear **Show \<***the information that you want***>**.  
  
## <a name="bkmk_symbols"></a> Load Symbols for a module
In the **Call Stack** window, you can load debugging symbols for code that does not currently have symbols loaded. These symbols can be .NET Framework or system symbols downloaded from the Microsoft public symbol servers or symbols in a symbol path on the computer that you are debugging.  
  
See [Specify Symbol (.pdb) and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>To load symbols  
  
1.  In the **Call Stack** window, right-click the stack frame for which symbols are not loaded. The frame will be dimmed.  
  
2.  Point to **Load Symbols** and then click **Microsoft Symbol Servers** (if available) or browse to the symbol path.  
  
### <a name="to-set-the-symbol-path"></a>To set the symbol path  
  
1.  In the **Call Stack** window, choose **Symbol Settings** from the shortcut menu.  
  
     The **Options** dialog box opens and the **Symbols** page is displayed.  
  
2.  Click **Symbol Settings**.  
  
3.  In the **Options** dialog box, click the Folder icon.  
  
     In the **Symbol file (.pdb) locations** box, a cursor appears.  
  
4.  Type a directory pathname to the symbol location on the computer that you are debugging. For local and remote debugging, this is a path on your local computer.
  
5.  Click **OK** to close the **Options** dialog box.  
  
## <a name="see-also"></a>See Also  
 [Mixed Code and Missing Information in the Call Stack Window](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md) [Viewing Data in the Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specify Symbol (.pdb) and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Using Breakpoints](../debugger/using-breakpoints.md)