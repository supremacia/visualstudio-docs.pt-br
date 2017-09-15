---
title: 'Walkthrough: Displaying Signature Help | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: e3db1bec71ec34f35824c5a6f33e76fb3a9d522e
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-displaying-signature-help"></a>Walkthrough: Displaying Signature Help
Signature Help (also known as *Parameter Info*) displays the signature of a method in a tooltip when a user types the parameter list start character (typically an opening parenthesis). As a parameter and parameter separator (typically a comma) are typed, the tooltip is updated to show the next parameter in bold. You can define Signature Help in the context of a language service, or you can define your own file name extension and content type and display Signature Help for just that type, or you can display Signature Help for an existing content type (for example, "text"). This walkthrough shows how to display Signature Help for the "text" content type.  
  
 Signature Help is typically triggered by typing a specific character, for example, "(" (opening parenthesis), and dismissed by typing another character, for example, ")" (closing parenthesis). IntelliSense features that are triggered by typing a character can be implemented by using a command handler for the keystrokes (the <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) and a handler provider that implements the <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. To create the Signature Help source, which is the list of signatures that participate in Signature Help, implement the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface and a source provider that implements the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. The providers are Managed Extensibility Framework (MEF) component parts, and are responsible for exporting the source and controller classes and importing services and brokers, for example, the <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, which lets you navigate in the text buffer, and the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, which triggers the Signature Help session.  
  
 This walkthrough shows how to implement Signature Help for a hard-coded set of identifiers. In full implementations, the language is responsible for providing that content.  
  
## <a name="prerequisites"></a>Prerequisites  
 Starting in Visual Studio 2015, you do not install the Visual Studio SDK from the download center. It is included as an optional feature in Visual Studio setup. You can also install the VS SDK later on. For more information, see [Installing the Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creating a MEF Project  
  
#### <a name="to-create-a-mef-project"></a>To create a MEF project  
  
1.  Create a C# VSIX project. (In the **New Project** dialog, select **Visual C# / Extensibility**, then **VSIX Project**.) Name the solution `SignatureHelpTest`.  
  
2.  Add an Editor Classifier item template to the project. For more information, see [Creating an Extension with an Editor Item Template](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Delete the existing class files.  
  
4.  Add the following references to the project, and make sure **CopyLocal** is set to `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementing Signature Help Signatures and Parameters  
 The Signature Help source is based on signatures that implement <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, each of which contains parameters that implement <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. In a full implementation, this information would be obtained from the language documentation, but in this example, the signatures are hard-coded.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>To implement the Signature Help signatures and parameters  
  
1.  Add a class file and name it `SignatureHelpSource`.  
  
2.  Add the following imports.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]  [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Add a class named `TestParameter` that implements <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]  [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Add a constructor that sets all the properties.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]  [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Add the properties of <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]  [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Add a class named `TestSignature` that implements <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]  [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Add some private fields.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]  [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Add a constructor that sets the fields and subscribes to the <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> event.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]  [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Declare a `CurrentParameterChanged` event. This event is raised when the user fills in one of the parameters in the signature.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]   [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implement the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> property so that it raises the `CurrentParameterChanged` event when the property value is changed.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]  [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Add a method that raises the `CurrentParameterChanged` event.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]  [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Add a method that computes the current parameter by comparing the number of commas in the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> to the number of commas in the signature.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]  [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Add an event handler for the <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> event that calls the `ComputeCurrentParameter()` method.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]  [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implement the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> property. This property holds an <xref:Microsoft.VisualStudio.Text.ITrackingSpan> that corresponds to the span of text in the buffer to which the signature applies.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]  [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implement the other parameters.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]  [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementing the Signature Help Source  
 The Signature Help source is the set of signatures for which you provide information.  
  
#### <a name="to-implement-the-signature-help-source"></a>To implement the Signature Help source  
  
1.  Add a class named `TestSignatureHelpSource` that implements <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]  [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Add a reference to the text buffer.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]  [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Add a constructor that sets the text buffer and the Signature Help source provider.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]  [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implement the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> method. In this example, the signatures are hard-coded, but in a full implementation you would get this information from the language documentation.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]  [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  The helper method `CreateSignature()` is provided just for illustration.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]  [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implement the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> method. In this example, there are just two signatures, each of which has two parameters. Therefore, this method is not required. In a fuller implementation, in which more than one Signature Help source is available, this method is used to decide whether the highest-priority Signature Help source can supply a matching signature. If it cannot, the method returns null and the next-highest-priority source is asked to supply a match.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]  [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implement the Dispose() method:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]  [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementing the Signature Help Source Provider  
 The Signature Help source provider is responsible for exporting the Managed Extensibility Framework (MEF) component part and for instantiating the Signature Help source.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>To implement the Signature Help source provider  
  
1.  Add a class named `TestSignatureHelpSourceProvider` that implements <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, and export it with a <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> of "text", and an <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> of Before="default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]  [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implement <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> by instantiating the `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]  [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implementing-the-command-handler"></a>Implementing the Command Handler  
 Signature Help is typically triggered by a ( character and dismissed by a ) character. You can handle these keystrokes by implementing a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> so that it triggers a Signature Help session when it receives a ( character preceded by a known method name, and dismisses the session when it receives a ) character.  
  
#### <a name="to-implement-the-command-handler"></a>To implement the command handler  
  
1.  Add a class named `TestSignatureHelpCommand` that implements <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]  [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Add private fields for the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adapter (which lets you add the command handler to the chain of command handlers), the text view, the Signature Help broker and session, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, and the next <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]  [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Add a constructor to initialize these fields and to add the command filter to the chain of command filters.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]  [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implement the <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> method to trigger the Signature Help session when the command filter receives a ( character after one of the known method names, and to dismiss the session when it receives a ) character while the session is still active. In every case, the command is forwarded.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]  [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implement the <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> method so that it always forwards the command.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]  [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementing the Signature Help Command Provider  
 You can provide the Signature Help command by implementing the <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> to instantiate the command handler when the text view is created.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>To implement the Signature Help command provider  
  
1.  Add a class named `TestSignatureHelpController` that implements <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> and export it with the <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, and <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]  [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Import the <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (used to get the <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, given the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> object), the <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (used to find the current word), and the <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (to trigger the Signature Help session).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]  [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implement the <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> method by instantiating the `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]  [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="building-and-testing-the-code"></a>Building and Testing the Code  
 To test this code, build the SignatureHelpTest solution and run it in the experimental instance.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>To build and test the SignatureHelpTest solution  
  
1.  Build the solution.  
  
2.  When you run this project in the debugger, a second instance of Visual Studio is instantiated.  
  
3.  Create a text file and type some text that includes the word "add" plus an opening parenthesis.  
  
4.  After you type the opening parenthesis, you should see a tooltip that displays a list of the two signatures for the `add()` method.  
  
## <a name="see-also"></a>See Also  
 [Walkthrough: Linking a Content Type to a File Name Extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)