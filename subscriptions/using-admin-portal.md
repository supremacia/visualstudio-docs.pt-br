---
title: Usando o portal do administrador | Visual Studio Marketplace
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to manage your organization's Visual Studio subscriptions with the Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: cf44f74b32bd830c613adcc1ee35a95b97636772
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2017
---
#  <a name="using-the-visual-studio-subscriptions-administrator-portal"></a>Usando o portal do administrador de assinaturas do Visual Studio

Lembre-se disto ao usar o Portal de Administração de Assinaturas do Visual Studio:
 
- **As assinaturas do Visual Studio são licenciadas por usuário.** Cada assinante pode usar o software em quantos computadores forem necessários para desenvolvimento e teste. 
- **Atribua apenas um nível de assinatura para cada assinante**, correspondente à assinatura do Visual Studio comprada pela sua organização. Se houver assinantes com mais de um nível de assinatura atribuído, edite as configurações para que eles fiquem com apenas uma. 
- **O nível de assinatura de um assinante precisará ser atualizado** quando a assinatura for atualizada (após a compra de um licença de “step-up”) ou renovada para um nível inferior. 
- **Não compartilhe assinaturas entre assinantes.** Você deverá atribuir uma assinatura a qualquer pessoa que usar completa ou parcialmente os benefícios da assinatura (software para desenvolvimento e teste, Microsoft Azure, e-learning, etc.). 

## <a name="adminstrator-roles"></a>Funções de administrador
Há duas funções diferentes no novo Portal de Administração de Assinaturas do Visual Studio para clientes do Volume Licensing. Essas funções são como a função de contato principal/para notificações e a função de gerenciador de assinaturas que existem atualmente no VLSC. 

**Superadministradores:** ao configurar uma organização pela primeira vez, o contato principal ou para notificações torna-se um superadministrador por padrão. O contato principal ou para notificações pode optar por atribuir superadministradores ou administradores adicionais. Um superadministrador pode adicionar e remover outros administradores e também assinantes. Se houver mais de dois superadministradores no sistema, um superadministrador poderá excluir todos, exceto os dois últimos por segurança. 

**Administradores:** um administrador só pode ser configurado por um superadministrador. Um administrador pode gerenciar os assinantes nos contratos que o superadministrador atribui a ele. 

## <a name="getting-started"></a>Guia de Introdução
### <a name="onboarding"></a>Integração
Quando sua organização estiver pronta para ser integrada ao Portal de Administração de Assinaturas do Visual Studio, um email será enviado para os Contatos Principal e para Notificações convidando-os para concluir o processo de integração. Os detalhes abaixo são as etapas necessárias para realizar a integração no novo portal. Se você desejar um passo a passo do processo, confira este [vídeo de integração para o administrador](https://channel9.msdn.com/Series/Visual-Studio-Subscriptions-Administration/Onboarding-your-organization-to-the-new-Visual-Studio-Subscription-Administration-Portal-and-setting) ou este [artigo de suporte](https://support.microsoft.com/help/4013931/visual-studio-subscriptions-administrator-migration-process "Processo de migração do administrador de assinaturas do Visual Studio").   
1.  **Localizando o PCN e entrando:**
    - No email, os contatos principal e para notificações recebem um link exclusivo e os três últimos dígitos do PCN (Número do Cliente Público). * 
    - Para obter o PCN inteiro, o Contato principal precisará entrar no VLSC (instruções para localizar o PCN podem ser encontradas lá). 
    - Depois de obter o PCN, ele precisará selecionar o link exclusivo que permitirá sua entrada. Ele poderá entrar usando uma conta corporativa ou de estudante (se sua organização estiver no AAD) ou uma conta MSA (conta da Microsoft) se sua organização não estiver no AAD. 
    - Em seguida, será necessário inserir o PCN. 
2.  **Configure seus administradores.** Depois de inserir o PCN, ele será registrado como um superadministrador no novo sistema e poderá adicionar outros superadministradores e administradores (conhecidos anteriormente como gerentes de assinatura). Para evitar a perda do acesso, isso deverá ser concluído antes da data de migração da organização. 
3.  **Acessando o novo portal de gerenciamento de assinaturas.**  Depois da migração da organização, serão enviados emails para os superadministradores e administradores recém-adicionados convidando-os para acessar o novo portal e começar a gerenciar assinaturas.  

* *Observação: se os contatos principal e para notificações receberem mais de um email, isso significará que eles têm mais de um PCN. Será necessário concluir o processo usando o link exclusivo para o PCN referenciado em cada email.*

Se você precisar ser adicionado no novo Portal de Administração de Assinaturas do Visual Studio e não souber quem é seu contato principal/para notificações, você poderá encontrar essa informação depois de entrar no [VLSC](https://www.microsoft.com/Licensing/servicecenter/default.aspx). Confira [este artigo](https://www.visualstudio.com/subscriptions/support/locate-primary-contact/ "Como localizar meu contato principal?") para obter as etapas de como localizar seu contato principal/para notificações no VLSC.
Se você já foi configurado como administrador, acesse diretamente o [Portal de Administração de Assinaturas do Visual Studio](https://manage.visualstudio.com).

### <a name="understanding-the-subscribers-page"></a>Noções básicas sobre a página Assinantes
Depois que você atribuir as assinaturas, a guia Assinantes fornecerá informações detalhadas sobre seus assinantes, incluindo:
- O nome e o sobrenome de cada assinante.
- O endereço de email deste usuário.
- O nível de assinatura que foi atribuído.
- A data em que a assinatura foi atribuída. 
- A data de validade da assinatura.
- Uma descrição de texto opcional.
- Uma indicação se os downloads para o assinante foram habilitados ou desabilitados. 
- O país em que eles estão localizados.
- A preferência de idioma para o email de comunicação de atribuição do portal de administração.
- Um campo opcional para um endereço de email diferente usado para comunicações de conexão. 

No lado esquerdo dessa página, são exibidas informações adicionais sobre o número de licenças de assinatura compradas, atribuídas e ainda disponíveis na organização para cada contrato.

![Página Assinantes do Portal de Administração de assinaturas do Visual Studio](_img/using-admin-portal/subscribers-page.png)

### <a name="understanding-the-details-page"></a>Noções básicas sobre a página Detalhes
Para obter mais informações sobre o contrato exibido, selecione a guia Detalhes. Ela mostra o status do contrato, a conta da compra, os detalhes da organização, os contatos principais (do VLSC), os superadministradores (caso haja) e outras informações pertinentes.

![Página Detalhes do Portal de Administração de assinaturas do Visual Studio](_img/using-admin-portal/details-page.png)

