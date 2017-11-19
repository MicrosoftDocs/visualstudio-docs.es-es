---
title: FuncDebugEnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b81665c4709eb76b28f2e56dd83915fab66bbd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="funcdebugend"></a>FuncDebugEnd
Si una función tiene un punto definido en el que la depuración consiste en Finalizar, el punto de inicio de depuración se indican mediante un símbolo con un `SymTagFuncDebugEnd` etiqueta.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente muestra las propiedades que son válidas para este tipo de símbolo.  
  
|Propiedad|Tipo de datos|Descripción|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Desplazamiento de la parte de la ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte de la sección de ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Si la función utiliza una convención de llamada personalizada (sólo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Si la función realiza un retorno lejano (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Si la función contiene un retorno de la interrupción (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Si la función es estática (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la función envolvente.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Id. del símbolo léxico primario.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Dos puntos finales tienen una ubicación estática; Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Si la función se ha especificado con el [noinline](/cpp/cpp/noinline) atributo (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Si la función se ha especificado con el [noreturn](/cpp/cpp/noreturn) atributo (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Si nunca se llama a la función (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Desplazamiento de símbolos en memoria; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Si la función tiene información de depuración para el código optimizado (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posición relativa del final de esta función dentro de su módulo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagFuncDebugEnd` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posición de esta función en la imagen ejecutable.|  
  
## <a name="see-also"></a>Vea también  
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)