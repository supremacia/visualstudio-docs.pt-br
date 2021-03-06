---
title: "Obtendo uma lista de instalado trechos de código (o legados) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 53d0a4fc5abc43bc446b3523cc7e8075eb7d4aa9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Passo a passo: Obtendo uma lista de trechos de código instalado (herdado de implementação)
Um trecho de código é um trecho de código que pode ser inserido no buffer de origem com um comando de menu (o que permite escolher entre uma lista de trechos de código instalado) ou por um atalho de trecho de código a seleção de uma lista de conclusão do IntelliSense.  
  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> método obtém todos os trechos de código para um idioma específico GUID. Os atalhos para os trechos de código podem ser inseridos em uma lista de conclusão do IntelliSense.  
  
 Consulte [suporte para trechos de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) para obter detalhes sobre a implementação de trechos de código em um serviço de idioma do pacote gerenciado framework (MPF).  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Para recuperar uma lista de trechos de código  
  
1.  O código a seguir mostra como obter uma lista de trechos de código para um determinado idioma. Os resultados são armazenados em uma matriz de <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> estruturas. Esse método usa estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método para obter o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> de interface do <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> service. No entanto, você também pode usar o provedor de serviço fornecido ao seu VSPackage e chamar o <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> método.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Para chamar o método GetSnippets  
  
1.  O método a seguir mostra como chamar o `GetSnippets` método na conclusão de uma operação de análise. O <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> método é chamado após uma operação de análise que foi iniciada com a razão <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  O `expansionsList` listis armazenado em cache por motivos de desempenho de matriz. As alterações para os trechos de código não são refletidas na lista até que o serviço de linguagem é interrompido e recarregado (por exemplo, ao parar e reiniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Para usar as informações de trecho de código  
  
1.  O código a seguir mostra como usar as informações de trecho de código retornadas pelo `GetSnippets` método. O `AddSnippets` método é chamado de analisador em resposta a qualquer razão de análise que é usado para preencher uma lista de trechos de código. Isso deve ocorrer após a análise completa pela primeira vez.  
  
     O `AddDeclaration` cria uma lista de declarações é exibida posteriormente em uma lista de conclusão.  
  
     O `TestDeclaration` classe contém todas as informações que podem ser exibidas em uma lista de conclusão, bem como o tipo de declaração.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a trechos de código em um serviço de linguagem herdado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)