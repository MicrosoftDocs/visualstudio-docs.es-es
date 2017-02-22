---
title: "CompilandDetails | Microsoft Docs"
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
  - "CompilandDetails (símbolo)"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La información de Compilación se divide entre los símbolos con una etiqueta de `SymTagCompiland` \(detalle en\) y una etiqueta de `SymTagCompilandDetails` \(alto detalle\).  `SymTagCompilandDetails` requiere cargar símbolos adicionales.  Sin embargo, proporciona una gran cantidad de información sobre la compilación que no está disponible con un símbolo de `SymTagCompiland` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades que son válidas para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Número de compilación back\-end del compilador.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Centralice el número de versión principal del compilador.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versión secundaria back\-end del compilador.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nombre del compilador que generó esta compilación \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` si editar y continuar se habilitados en la compilación.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilación front\-end del compilador.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Número de versión principal front\-end del compilador.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versión secundaria front\-end del compilador.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` si este compilación tiene información de depuración \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` si este compilación contiene código administrado \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si la compilación fue compilado con el modificador del compilador [\/GS \(Comprobación de seguridad del búfer\)](/visual-cpp/build/reference/gs-buffer-security-check) \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` si el compilando se convirtió de código de lenguaje intermedio común \(CIL\) a código nativo.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` si los tipos definidos \(UDT\) por el usuario se han alineado al límite especificado de memoria \(sólo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` si la compilación fue compilado con el modificador del compilador [\/hotpatch \(Crear una imagen a la que se puede aplicar una revisión reciente\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` si la compilación fue compilado con el modificador del compilador [\/LTCG \(Generación de código en tiempo de enlace\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) \(solo en el diámetro SDK V8.0 o posterior\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si la compilación es un módulo de Lenguaje intermedio de Microsoft \(MSIL\) \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|lenguaje de código fuente.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo para la compilación.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma en la que el compilando fue compilado \(uno de los valores de [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md) \).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagCompilandDetails` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Comentarios  
 Los compiladores suelen presentarse en un formulario conocido como el compilador de dos pasos; en algunas versiones del compilador, cada paso lo controla un programa independiente.  Éstos se conocen como front\-end y compiladores de back\-end, respectivamente, por tanto las propiedades de símbolos para los números de versión back\-end y front\-end.  
  
## Vea también  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)