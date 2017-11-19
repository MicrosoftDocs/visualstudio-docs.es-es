---
title: "Función (Debug Interface Access SDK) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39d3871fcfbd3702e2ad198f2061be41dc51ac18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="function-debug-interface-access-sdk"></a>Función (Debug Interface Access SDK)
Cada función se identifica mediante un `SymTagFunction` símbolos.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente muestra las propiedades que son válidas para este tipo de símbolo.  
  
|Propiedad|`Data type`|Descripción|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Uno de los valores de la [CV_access_e (enumeración)](../../debugger/debug-interface-access/cv-access-e.md), si la función es una función miembro.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Desplazamiento de la parte de la ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte de la sección de ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Símbolo de la clase, si la función es una función miembro.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Id. del símbolo de elemento primario de clase.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`Si la función está marcada como una constante.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Si la función utiliza una convención de llamada personalizada (sólo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Si la función realiza un retorno lejano (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE`Si la función utiliza la función de la memoria asignada (solo uinnder V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE`Si la función contiene (solo en V8.0 de SDK de DIA o posterior) de control de excepciones de tipo C++.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE`Si la función contiene el control de excepciones asincrónicas (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE`Si la función contiene código ensamblador en línea (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE`Si la función contiene un [longjmp](/cpp/c-runtime-library/reference/longjmp) llamar (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`Si la función contiene comprobaciones de seguridad (sólo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE`Si la función contiene (solo en V8.0 de SDK de DIA o posterior) del control de excepciones estructurado en el estilo de Win32.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE`Si la función contiene un [setjmp](/cpp/c-runtime-library/reference/setjmp) llamar (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Si la función tiene una devolución de interrupción (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE`Si una función es preliminar virtual.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE`Si la función se ha marcado con uno de los [inline, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp.md) atributos.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE`Si la función se marca con la [naked](/cpp/cpp/naked-cpp) atributo (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Si la función es estática (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Número de bytes de código de la función, a partir de la ubicación.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación envolvente.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Id. del símbolo léxico primario.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Las funciones pueden tener ubicaciones estático o de metadatos; Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre de la función.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Si la función no es una función insertada (solo V8.0 n de SDK de DIA o posterior).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Si la función no es accesible (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Si la función no devuelve un valor (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE`Si la función se compiló con las comprobaciones de seguridad de búfer, pero ninguna pila ordenación puede realizarse.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Si el código tiene información de depuración para el código optimizado (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE`Si la función es pura virtual.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posición relativa de esta función dentro de su módulo.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagFunction` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Símbolo (token) de metadatos para la función.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Símbolo de la firma de función.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Id. del símbolo de tipo.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`Si la función se desalineadas.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|El formato no representativo del nombre de función (solo en el SDK de DIA v8.0 o posterior)|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Parte o la totalidad de la forma no representativa del nombre de función (solo en el SDK de DIA v8.0 o posterior).|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`Si una función virtual.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posición de esta función en la imagen ejecutable.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Si una función virtual, a continuación, el desplazamiento en la tabla de funciones virtuales.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Si la función está marcada como volátil.|  
  
## <a name="see-also"></a>Vea también  
 [CV_access_e (enumeración)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)