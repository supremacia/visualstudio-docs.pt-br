---
title: "Compatibilidade de versão para políticas do Check-In de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 323024cdb420d48c40b7a676bc4e698af7622b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilidade da versão para políticas de check-in de análise do código
Se você deve avaliar e criar usam versões diferentes das políticas de seleção da análise de código [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], você deve saber as diferenças em como [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] e [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] avaliar políticas de check-in.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilidade de versão para avaliar as políticas de Check-In  
  
-   Quando as políticas do check-in de análise de código são avaliadas em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], todas as regras que existiam na [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , mas não existem no [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] são ignorados.  
  
-   Quando as políticas do check-in de análise de código são avaliadas em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], todas as novas regras que são exclusivas para [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] são ignorados.  
  
-   Se a política de check-in do análise código especifica os assemblies de regras, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignora todas as regras que são especificadas por assemblies que não reconhece.  
  
-   Se a política de check-in do análise código especifica os assemblies de regras que [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] não reconhece, será exibida uma mensagem.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilidade de versão para a criação de políticas de Check-In  
  
-   Se você criou uma política de check-in do analysis código usando o [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] versão do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], você não pode usar o [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] versão do [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] modificá-lo. E também, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] não é possível avaliar a política.  
  
-   Se você criou uma política de check-in do analysis código usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] na [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], você pode usar [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] na [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] modificar e a política também pode ser avaliada pelo [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Depois de modificar a política usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] na [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você não pode editar a política usando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]pode avaliar essas políticas sem problemas com nomes fortes incompatíveis.  
  
-   Para criar uma política de check-in do analysis código com configurações de regra que se aplicam a ambos [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] e [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você deve criar a política em [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], faça todas as alterações necessárias e salve a política. Se as alterações às regras só existem em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], modificar e salvar a política em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].  
  
     Depois de salvar a política em [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], você não pode alterar as configurações para regras que existem no [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] somente.