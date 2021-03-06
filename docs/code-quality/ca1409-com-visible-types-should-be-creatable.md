---
title: "CA1409: Os tipos visíveis Com devem ser instanciáveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f12dda380f887aca50b764d0ec20f9db1c0cd07c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: os tipos visíveis Com devem ser criáveis
|||  
|-|-|  
|NomeDoTipo|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo de referência é especificamente marcado como visível para o modelo de objeto componente (COM) contém um construtor parametrizado público, mas não tem um construtor público padrão (sem parâmetros).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um tipo sem um construtor padrão público não pode ser criado por clientes COM. No entanto, o tipo ainda pode ser acessado por clientes COM se houver outros meios criar o tipo e passá-lo para o cliente (por exemplo, por meio do valor de retorno de uma chamada de método).  
  
 A regra ignora os tipos que são derivados de <xref:System.Delegate?displayProperty=fullName>.  
  
 Por padrão, os seguintes são visíveis no COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione um construtor padrão público ou remova o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> do tipo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se outros modos são fornecidos para criar e passar o objeto para o cliente COM.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Consulte também  
 [Qualificando tipos do .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)