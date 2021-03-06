---
title: "Símbolos locais | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a4cd226ebc3d2853ddfa35f42c5990db940c4424
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-locations"></a>Locais de símbolos
A maioria dos símbolos tem um local definido dentro do arquivo de imagem. Local do símbolo é especificado com um valor da [enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) enumeração. O símbolo pode oferecer suporte a propriedades adicionais, dependendo de seu local.  
  
 A tabela a seguir mostra os mais usados tipos de local e suas propriedades adicionais.  
  
|Tipo de local|Propriedades adicionais|  
|-------------------|---------------------------|  
|`LocIsNull`|nenhum|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (se relativo endereços virtuais estão habilitados)<br /><br /> [: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (se a base de imagem tenha sido definida como diferente de zero)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Consulte também  
 [: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [: Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [: Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Idiasymbol](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [: Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [: Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [: Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [: Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)