---
title: Elemento KeyBinding | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2019a34e55148007cd75df12212bd4b0a897159c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="keybinding-element"></a>Elemento KeyBinding
O elemento KeyBinding Especifica atalhos de teclado para os comandos.  
  
 Comandos podem ter associações de chave única e duplas associadas a eles. Um exemplo de uma única chave de associação é CTRL + S para o **salvar** comando. Associações de chave duplas exigem duas combinações de teclas sucessivas para disparar um comando. Um exemplo de uma associação de chave dupla é CTRL + K, CTRL + K para definir um indicador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário.|  
|id|Necessário.|  
|editor|Necessário. O GUID do editor indica o contexto de edição para o qual este atalho de teclado ficará ativo. O valor de escopo global de associação é "guidVSStd97".|  
|Key1|Necessário. Os valores válidos incluem todos os typable alfanuméricos e valores hexadecimais de dois dígitos precedidos por 0x e [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|Mod1|Opcional. Qualquer combinação de CTRL, ALT e SHIFT separadas por espaço.|  
|Key2|Opcional. Os valores válidos incluem todos os typable alfanuméricos e valores hexadecimais de dois dígitos precedidos por 0x e [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|Mod2|Opcional. Qualquer combinação de CTRL, ALT e SHIFT separadas por espaço.|  
|emulador|Opcional.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Pai||  
|Anotação||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Agrupa elementos de KeyBinding e outros agrupamentos de associações.|  
  
## <a name="example"></a>Exemplo  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento de associações](../extensibility/keybindings-element.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
