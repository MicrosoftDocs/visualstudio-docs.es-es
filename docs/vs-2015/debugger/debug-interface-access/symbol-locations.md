---
title: Ubicaciones de símbolos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dffab87abed5bb8187a5340955dea84f77ccab8f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582835"
---
# <a name="symbol-locations"></a>Symbol Locations
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ubicaciones de símbolos](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/symbol-locations).  
  
La mayoría de los símbolos con una ubicación definida dentro del archivo de imagen. Se especifica la ubicación de un símbolo con un valor de la [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) enumeración. El símbolo puede admitir propiedades adicionales según su ubicación.  
  
 En la tabla siguiente se muestra la mayoría usadas habitualmente los tipos de ubicación y sus propiedades adicionales.  
  
|Tipo de ubicación|Propiedades adicionales|  
|-------------------|---------------------------|  
|`LocIsNull`|ninguna|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (si están habilitadas las direcciones virtuales relativas)<br /><br /> [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (si se ha establecido distinto de cero a la base de imagen)|  
|`LocIsTLS`|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|  
|`LocIsBitField`|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## <a name="see-also"></a>Vea también  
 [Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)



