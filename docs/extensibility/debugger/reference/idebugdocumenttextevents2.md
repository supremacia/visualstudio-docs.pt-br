---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2
helpviewer_keywords: IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb9e284435cdf8a5905e068b0044cd118a1621c9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Essa interface é usada para notificar o Visual Studio sobre alterações para o documento de origem que são fornecidas pelo mecanismo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para oferecer suporte a fazer alterações ao código-fonte. Normalmente, essa interface é implementada no mesmo objeto que implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Obtém a esta interface por meio de uma chamada para o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método. O <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface é obtida de uma chamada para o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> método. O <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface é obtida chamando o [QueryInterface](/cpp/atl/queryinterface) método em um [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugDocumentTextEvents2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que todo o documento foi destruído.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica o pacote de depuração que o texto foi inserido no documento.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica o pacote de depuração que o texto foi removido do documento.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica o pacote de depuração que o texto foi substituído no documento.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica o pacote de depuração que atributos de texto foram atualizados no documento.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica o receptor do evento que os atributos do documento foram atualizados.|  
  
## <a name="remarks"></a>Comentários  
 Somente os mecanismos de depuração que fornecem seus próprios documentos seriam aproveitar o `IDebugDocumentTextEvent2` interface. Um exemplo disso seria um mecanismo de depuração de script. No processo de interpretar scripts, novo código-fonte pode ser gerado que não está presente em qualquer arquivo de disco e é conhecido apenas DE.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)