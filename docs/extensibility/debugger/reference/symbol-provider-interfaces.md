---
title: "Interfaces de provedor de símbolo | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3fe7e2c641cb407f03557a555e5a66abe5cea367
ms.lasthandoff: 02/22/2017

---
# <a name="symbol-provider-interfaces"></a>Interfaces de provedor de símbolo
A seguir estão as Interfaces de tratamento de símbolo para o [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Discussão  
 Essas interfaces são usadas para avaliar as variáveis em uma pilha de chamadas durante o modo de interrupção. Eles são implementados somente para provedores de símbolo de tempo de execução de linguagem comum (SP).  
  
|Interface|Implementado por|Descrição|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Representa o endereço de um item.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Representa o endereço de um item, fornecendo acesso a ID de processo.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Representa um tipo de matriz ou um símbolo de matriz.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Representa um símbolo de classe ou tipo de classe.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Representa um provedor de símbolo COM+ com métodos que são específicos para o código gerenciado.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Representa um provedor de símbolo COM+ com métodos que são específicos para o código gerenciado e estende o **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Representa um símbolo ou um tipo que é um contêiner para outros símbolos ou tipos.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Representa um atributo personalizado que pode ser anexado a um símbolo.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Representa uma consulta para atributos personalizados em um tipo ou método.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Fornece acesso a atributos personalizados em um símbolo.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|A interface base para qualquer tipo que pode ser determinada em tempo de execução.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Representa um campo dinâmico para um [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Representa um tipo de enumeração.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Pa|Estende os tipos de campos disponíveis para oferecer suporte a genéricos de código gerenciado.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|A classe base para todos os campos; representa uma descrição de um símbolo ou tipo.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Representa a definição de um campo de um tipo genérico de código gerenciado.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Representa uma instância de um campo de um tipo genérico de código gerenciado.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Representa um parâmetro para um tipo genérico de código gerenciado.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Representa um método.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Representa um modificador opcional de depuração.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Representa um ponteiro.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Representa um valor de enumeração de tipo primitivo de uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Representa uma propriedade de uma classe de código gerenciado que pode ser get ou definido.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Representa um provedor de símbolo que fornece tipos e símbolos.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Representa um provedor de símbolo com acesso direto a metadados e principais interfaces de símbolo.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Representa a capacidade de criar um campo que representa um tipo.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende o **IDebugTypeFieldBuilder** para poder criar tipos de matriz.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Representa uma coleção de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Representa uma coleção de [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objetos.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Representa uma coleção de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)