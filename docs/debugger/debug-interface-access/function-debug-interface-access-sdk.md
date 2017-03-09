---
title: "Funci&#243;n (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "símbolo de función"
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funci&#243;n (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada función se indican mediante un símbolo de `SymTagFunction` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades que son válidas para este tipo de token.  
  
|Propiedad.|`Data type`|Descripción|  
|----------------|-----------------|-----------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Uno de los valores de [CV\_access\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-access-e.md), si la función es una función miembro.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|desplazamiento de ubicación; para obtener información detallada, vea [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte de la sección de ubicación; para obtener información detallada, vea [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Token para la clase, si la función es una función miembro.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identificador del elemento primario de la clase.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la función se marca como constante.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` si la función utiliza una convención de llamada personalizada \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` si la función realiza un aún return \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` si la función utiliza la función de la memoria asignada \(solo diámetro SDK V8.0 de uinnder o posterior\).|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` si la función contiene el control de excepciones estilos de C\+\+ \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` si la función contiene administrar asincrónico de excepción \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` si la función contiene el ensamblado en línea \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` si la función contiene una llamada de [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si la función contiene comprobaciones de seguridad \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` si la función contiene el control de excepciones estructurado de estilo Win32 \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` si la función contiene una llamada de [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` si la función tiene un retorno de la interrupción \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` si una función es introducción virtual.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` si la función está marcado con uno de los atributos de [inline, \_\_inline, \_\_forceinline](../../misc/inline-inline-forceinline.md) .|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` si la función se marca con el atributo de [naked](/visual-cpp/cpp/naked-cpp) \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` si la función es estática \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Número de bytes de código de función, a partir de la ubicación.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de compilación envolvente.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Las funciones pueden tener ubicaciones de estático o de metadatos; para obtener información detallada, vea [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre de la función.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` si la función no es una función inline \(solo diámetro SDK V8.0 n o posterior\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` si la función no es accesible \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` si la función no devuelve un valor \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` si la función es compilada con las comprobaciones de seguridad del búfer pero ningún orden de pila podría hacer.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` si el código tiene información de depuración para el código optimizado \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` si la función es virtual pura.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posición relativa de esta función dentro del módulo.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagFunction` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Metadatos de para la función.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Token para la firma de la función.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identificador del tipo.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la función es sin alinear.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|El formato representativo del nombre de función \(solo en el diámetro SDK v8.0 o posterior\)|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Parte o todo el formulario representativo del nombre de función \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` si una función virtual.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|posición de esta función dentro de la imagen ejecutable.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Si una función virtual, el desplazamiento en la tabla de función virtual.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la función se marca como tal.|  
  
## Vea también  
 [CV\_access\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md)   
 [Symbol Locations](../../debugger/debug-interface-access/symbol-locations.md)