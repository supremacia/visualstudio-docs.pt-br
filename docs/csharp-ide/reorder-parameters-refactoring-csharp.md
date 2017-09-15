---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: Reorder Parameters Refactoring (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
manager: wpickett
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 76fb3d24801d2f5fc04f4fc349080ee643e39f76
ms.contentlocale: pt-br
ms.lasthandoff: 08/28/2017

---
# <a name="reorder-parameters-refactoring-c"></a>Reorder Parameters Refactoring (C#)
`Reorder Parameters` is a Visual C# refactoring operation that provides an easy way to change the order of the parameters for methods, indexers, and delegates. `Reorder Parameters` changes the declaration, and at any locations where the member is called, the parameters are rearranged to reflect the new order.  
  
 To perform the `Reorder Parameters` operation, put the cursor on or next to a method, indexer, or delegate. When the cursor is in position, invoke the `Reorder Parameters` operation by pressing the keyboard shortcut, or by clicking the command from the shortcut menu.  
  
> [!NOTE]
>  You cannot reorder the first parameter in an extension method.  
  
### <a name="to-reorder-parameters"></a>To reorder parameters  
  
1.  Create a class library named `ReorderParameters`, and then replace `Class1` with the following example code.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Place the cursor on `MethodB`, either in the method declaration or the method call.  
  
3.  On the **Refactor** menu, click **Reorder Parameters**.  
  
     The **Reorder Parameters** dialog box appears.  
  
4.  In the **Reorder Parameters** dialog box, select `int i` in the **Parameters** list, and then click the down button.  
  
     Alternatively, you can drag `int i` after `bool b` in the **Parameters** list.  
  
5.  In the **Reorder Parameters** dialog box, click **OK**.  
  
     If the **Preview reference changes** option is selected in the **Reorder Parameters** dialog box, the **Preview Changes - Reorder Parameters** dialog box will appear. It provides a preview of the changes in the parameter list for `MethodB` in both the signature and the method call.  
  
    1.  If the **Preview Changes - Reorder Parameters** dialog box appears, click **Apply**.  
  
         In this example, the method declaration and all the method call sites for `MethodB` are updated.  
  
## <a name="remarks"></a>Remarks  
 You can reorder parameters from a method declaration or a method call. Position the cursor on or next to the method or delegate declaration but not in the body.  
  
## <a name="see-also"></a>See Also  
 [Refactoring (C#)](refactoring-csharp.md)