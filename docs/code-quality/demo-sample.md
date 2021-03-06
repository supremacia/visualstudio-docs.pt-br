---
title: "Exemplo de demonstração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be42ed54e2c245a47e885fe8310c106c27ea82b2
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="demo-sample"></a>Amostra de demonstração
Este procedimentos a seguir mostram como criar o exemplo do [passo a passo: Analisando código C/C++ em busca de defeitos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Criam os procedimentos:  
  
-   Um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução nomeada CppDemo.  
  
-   Um projeto de biblioteca estática denominada CodeDefects.  
  
-   Um projeto de biblioteca estática chamada anotações.  
  
 Os procedimentos também fornecem o código para os arquivos de cabeçalho e. cpp para as bibliotecas estáticas.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Criar a solução CppDemo e o projeto CodeDefects  
  
1.  Clique o **arquivo** , aponte para **novo**e, em seguida, clique em **novo projeto**.  
  
2.  No **tipos de projeto** lista de árvore, expanda se Visual C++ não é o idioma padrão no VS **outras linguagens**.  
  
3.  Expanda **Visual C++**e, em seguida, clique em **geral**.  
  
4.  Em **modelos**, clique em **projeto vazio**.  
  
5.  No **nome** caixa de texto, digite **CodeDefects**.  
  
6.  Marque a caixa de seleção **Criar diretório para a solução**.  
  
7.  No **nome da solução** caixa de texto, digite **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurar o projeto CodeDefects como uma biblioteca estática  
  
1.  No Gerenciador de soluções, clique com botão direito **CodeDefects** e, em seguida, clique em **propriedades**.  
  
2.  Expanda **propriedades de configuração** e, em seguida, clique em **geral**.  
  
3.  No **geral** , selecione o texto na coluna ao lado **extensão de destino**e, em seguida, digite **. lib**.  
  
4.  Em **padrões do projeto**, clique na coluna ao lado **tipo de configuração**e, em seguida, clique em **biblioteca estática (. lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Adicione o arquivo de cabeçalho e fonte ao projeto CodeDefects  
  
1.  No Gerenciador de soluções, expanda **CodeDefects**, clique com botão direito **arquivos de cabeçalho**, clique em **adicionar**e, em seguida, clique em **Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, clique em **código**e, em seguida, clique em **o arquivo de cabeçalho (. h)**.  
  
3.  No **nome** , digite **Bug.cpp** e, em seguida, clique em **adicionar**.  
  
4.  Copie o código a seguir e cole-o no **Bug.cpp** arquivo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  No Gerenciador de soluções, clique com botão direito **arquivos de origem**, aponte para **novo**e, em seguida, clique em **Novo Item**.  
  
6.  No **Adicionar Novo Item** caixa de diálogo, clique em **C++ arquivo (. cpp)**  
  
7.  No **nome** , digite **Bug.cpp** e, em seguida, clique em **adicionar**.  
  
8.  Copie o código a seguir e cole-o no arquivo Bug.h do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Clique o **arquivo** menu e clique **Salvar tudo**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Adicione o projeto de anotações e configurá-lo como uma biblioteca estática  
  
1.  No Gerenciador de soluções, clique em **CppDemo**, aponte para **adicionar**e, em seguida, clique em **novo projeto**.  
  
2.  No **adicionar novo projeto** caixa de diálogo, expanda o Visual C++, clique em **geral**e, em seguida, clique em **projeto vazio**.  
  
3.  No **nome** caixa de texto, digite **anotações**e, em seguida, clique em **adicionar**.  
  
4.  No Gerenciador de soluções, clique com botão direito **anotações** e, em seguida, clique em **propriedades**.  
  
5.  Expanda **propriedades de configuração** e, em seguida, clique em **geral**.  
  
6.  No **geral** , selecione o texto na coluna ao lado **extensão de destino**e, em seguida, digite **. lib**.  
  
7.  Em **padrões do projeto**, clique na coluna ao lado **tipo de configuração**e, em seguida, clique em **biblioteca estática (. lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Adicionar o arquivo de cabeçalho e o arquivo de origem para o projeto de anotações  
  
1.  No Gerenciador de soluções, expanda **anotações**, clique com botão direito **arquivos de cabeçalho**, clique em **adicionar**e, em seguida, clique em **Novo Item**.  
  
2.  No **Adicionar Novo Item** caixa de diálogo, clique em **o arquivo de cabeçalho (. h)**.  
  
3.  No **nome** , digite **annotations.h** e, em seguida, clique em **adicionar**.  
  
4.  Copie o código a seguir e cole-o no **annotations.h** arquivo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  No Gerenciador de soluções, clique com botão direito **arquivos de origem**, aponte para **novo**e, em seguida, clique em **Novo Item**.  
  
6.  No **Adicionar Novo Item** caixa de diálogo, clique em **código** e, em seguida, clique em **C++ arquivo (. cpp)**  
  
7.  No **nome** , digite **annotations.cpp** e, em seguida, clique em **adicionar**.  
  
8.  Copie o código a seguir e cole-o no **annotations.cpp** arquivo o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Clique o **arquivo** menu e clique **Salvar tudo**.