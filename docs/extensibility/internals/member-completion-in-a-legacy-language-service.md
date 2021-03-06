---
title: "Conclusão de membro em um serviço de linguagem herdado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e77511bdaaa96dc75f5be75c175b63fcd3cc3253
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="member-completion-in-a-legacy-language-service"></a>Conclusão de membro em um serviço de linguagem herdado
A conclusão do IntelliSense membro é uma dica de ferramenta que exibe uma lista de possíveis membros de um escopo específico, como uma classe, estrutura, enumeração ou namespace. Por exemplo, no c#, se o usuário digitar "this" seguido por um período, uma lista de todos os membros da classe ou estrutura no escopo atual é apresentada em uma lista na qual o usuário pode selecionar.  
  
 A estrutura de pacote gerenciado (MPF) fornece suporte para a dica de ferramenta e o gerenciamento da lista na dica de ferramenta; tudo o que é necessário é cooperação do analisador para fornecer os dados que aparecem na lista.  
  
 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente para implementar recursos de serviço de linguagem é usar extensões MEF. Para obter mais informações, consulte [estendendo o Editor e o idioma serviços](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  É recomendável que você comece a usar o novo editor de API assim que possível. Isso melhorar o desempenho do seu serviço de linguagem e permitem que você aproveite os novos recursos do editor.  
  
## <a name="how-it-works"></a>Como ele funciona  
 Estas são as duas maneiras em que uma lista de membros é mostrada usando as classes MPF:  
  
-   Posicionando o cursor em um identificador ou depois de um caractere de preenchimento de membro e selecionando **lista membros** do **IntelliSense** menu.  
  
-   O <xref:Microsoft.VisualStudio.Package.IScanner> scanner detecta um caractere de preenchimento de membro e define um gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers> para esse caractere.  
  
 Um caractere de preenchimento do membro indica que um membro de classe, estrutura ou enumeração é a seguir. Por exemplo, em c# ou Visual Basic o caractere de preenchimento do membro é um `.`, enquanto em C++ o caractere é um `.` ou `->`. O valor de gatilho é definido quando o caractere de seleção de membro é verificado.  
  
### <a name="the-intellisense-member-list-command"></a>O comando de lista de membros do IntelliSense  
 O <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando inicia uma chamada para o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método o <xref:Microsoft.VisualStudio.Package.Source> classe e o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, por sua vez, chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analisador de método com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 O analisador determina o contexto de posição atual, bem como o token em ou imediatamente antes da posição atual. Com base nesse token, é apresentada uma lista de declarações. Por exemplo, no c#, se você posicionar o cursor em um membro de classe e selecione **lista membros**, você obtém uma lista de todos os membros da classe. Se você posicionar o cursor depois de um período que segue uma variável de objeto, você pode obter uma lista de todos os membros da classe que o objeto representa. Observe que se o cursor estiver posicionado em um membro quando a lista de membros é mostrada, selecionando um membro da lista substitui o membro que o cursor estiver em uma na lista.  
  
### <a name="the-token-trigger"></a>O gatilho de Token  
 O <xref:Microsoft.VisualStudio.Package.TokenTriggers> gatilho inicia uma chamada para o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método no <xref:Microsoft.VisualStudio.Package.Source> classe e o <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> método, por sua vez, chama o analisador com a razão de análise de <xref:Microsoft.VisualStudio.Package.ParseReason> (se o token gatilho incluídos também o <xref:Microsoft.VisualStudio.Package.TokenTriggers> sinalizador o motivo de análise é <xref:Microsoft.VisualStudio.Package.ParseReason> que combina a seleção de membro e realce de chave).  
  
 O analisador determina o contexto atual posição, bem como o que foi digitado para o membro selecionar caractere. Essas informações, o analisador cria uma lista de todos os membros do escopo solicitado. Essa lista de declarações é armazenada no <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto que é retornado o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método. Se todas as declarações são retornadas, a dica de ferramenta de conclusão de membro será exibida. A dica de ferramenta é gerenciada por uma instância de <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
## <a name="enabling-support-for-member-completion"></a>Habilitar o suporte para a conclusão de membro  
 Você deve ter o `CodeSense` entrada do registro é definida como 1 para dar suporte a qualquer operação do IntelliSense. Essa entrada do registro pode ser definida com um parâmetro nomeado passado para o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> associado com o pacote de idioma do atributo de usuário. As classes de serviço de linguagem ler o valor desta entrada do registro da <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> propriedade o <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Se o scanner retorna o token gatilho de <xref:Microsoft.VisualStudio.Package.TokenTriggers>e o analisador retorna uma lista de declarações, é exibida a lista de conclusão de membro.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Suporte a conclusão do membro no Scanner  
 O scanner deve ser capaz de detectar um caractere de preenchimento de membro e defina o gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando esse caractere é analisado.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo simplificado de detectar o caractere de preenchimento de membro e a configuração apropriada <xref:Microsoft.VisualStudio.Package.TokenTriggers> sinalizador. Este exemplo é apenas para fins ilustrativos. Ele pressupõe que o scanner contém um método `GetNextToken` que identifica e retornar tokens de uma linha de texto. O exemplo de código simplesmente define o gatilho sempre que ele vê o tipo correto de caractere.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Suporte a conclusão do membro no analisador  
 Para a conclusão de membro, o <xref:Microsoft.VisualStudio.Package.Source> classe chama o <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> método. Você deve implementar a lista em uma classe que deriva de <xref:Microsoft.VisualStudio.Package.Declarations> classe. Consulte o <xref:Microsoft.VisualStudio.Package.Declarations> classe para obter detalhes sobre os métodos que você deve implementar.  
  
 O analisador for chamado com <xref:Microsoft.VisualStudio.Package.ParseReason> ou <xref:Microsoft.VisualStudio.Package.ParseReason> quando um caractere de seleção de membro é digitado. O local especificado no <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é imediatamente após o membro selecionar caractere. O analisador deve coletar os nomes de todos os membros que podem aparecer em uma lista de membros em que ponto específico no código-fonte. Em seguida, o analisador deve analisar a linha atual para determinar o escopo em que o usuário deseja associado com o caractere de seleção de membro.  
  
 Esse escopo baseia-se no tipo do identificador antes que o membro selecionar caractere. Por exemplo, no c#, dado que a variável de membro `languageService` que tem um tipo de `LanguageService`, digitando **languageService.** gera uma lista de todos os membros de `LanguageService` classe. Também em c#, digitando **isso.** gera uma lista de todos os membros da classe no escopo atual.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma maneira de preencher um <xref:Microsoft.VisualStudio.Package.Declarations> lista. Esse código supõe que o analisador constrói uma declaração e o adiciona à lista chamando um `AddDeclaration` método sobre o `TestAuthoringScope` classe.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```