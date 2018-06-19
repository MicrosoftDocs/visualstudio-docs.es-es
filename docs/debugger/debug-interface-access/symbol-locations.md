---
title: Ubicaciones de símbolos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType values
- symbols [DIA SDK], locations
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 021911c01a7cd98e157f6c216ae28feffcaf7096
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480272"
---
# <a name="symbol-locations"></a>Symbol Locations
Símbolos mayoría tienen una ubicación definida en el archivo de imagen. Se especifica la ubicación de un símbolo con un valor comprendido entre el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) enumeración. El símbolo puede admitir las propiedades adicionales según su ubicación.  
  
 La siguiente tabla muestra usan con más frecuencia los tipos de ubicación y sus propiedades adicionales.  
  
|Tipo de ubicación|Propiedades adicionales|  
|-------------------|---------------------------|  
|`LocIsNull`|ninguna|  
|`LocIsStatic`|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [Idiasymbol:: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md) (si están habilitadas las direcciones virtuales relativas)<br /><br /> [Idiasymbol:: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md) (si se ha establecido es distinto de cero a la base de imagen)|  
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
 [Idiasymbol:: Get_addressoffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [Idiasymbol:: Get_addresssection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [Idiasymbol:: Get_bitposition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [Idiasymbol:: Get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Idiasymbol:: Get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [Idiasymbol:: Get_registerid](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)   
 [Idiasymbol:: Get_relativevirtualaddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [Idiasymbol:: Get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [Idiasymbol:: Get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [Idiasymbol:: Get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [Idiasymbol:: Get_virtualaddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)