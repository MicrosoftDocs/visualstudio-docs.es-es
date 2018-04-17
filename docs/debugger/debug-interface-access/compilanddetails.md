---
title: CompilandDetails | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16f9239028cada1108092af3bc5a511964f89c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="compilanddetails"></a>CompilandDetails
Información de la operación de compilación se divide entre los símbolos con un `SymTagCompiland` etiqueta (detalle baja) y un `SymTagCompilandDetails` etiqueta (detalles alto). `SymTagCompilandDetails` requiere la carga de símbolos adicionales. Sin embargo, proporciona una gran cantidad de información sobre la operación de compilación que no está disponible con un `SymTagCompiland` símbolos.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente muestra las propiedades que son válidas para este tipo de símbolo.  
  
|Property|Tipo de datos|Descripción|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Número de compilación de back-end del compilador.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Número de versión principal de back-end del compilador.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versión secundaria de back-end del compilador.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nombre del compilador que generó esta operación de compilación (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Si se habilitaron editar y continuar durante la compilación.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilación de front-end del compilador.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Número de versión principal front-end del compilador.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versión secundaria front-end del compilador.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Si esta operación de compilación tiene información de depuración (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Si esta operación de compilación contiene código administrado (sólo en el SDK de DIA v8.0 o posterior).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/GS (comprobación de seguridad de búfer)](/cpp/build/reference/gs-buffer-security-check) modificador del compilador (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Si la operación de compilación se convirtió desde el código de Common Intermediate Language (CIL) a código nativo.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Si los tipos definidos por el usuario (UDT) se ha alineado en algunos especificar límite de memoria (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/hotpatch (crear una imagen)](/cpp/build/reference/hotpatch-create-hotpatchable-image) modificador del compilador (solo en el SDK de DIA v8.0 o posterior).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/LTCG (generación de código de tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) modificador del compilador (solo en V8.0 de SDK de DIA o posterior).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Es TRUE si la operación de compilación es un módulo de lenguaje intermedio de Microsoft (MSIL) (solo en el SDK de DIA v8.0 o posterior).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Lenguaje del código fuente.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Id. del símbolo léxico primario.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma en la que se compiló la operación de compilación (uno de los [CV_CPU_TYPE_e (enumeración)](../../debugger/debug-interface-access/cv-cpu-type-e.md) valores).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagCompilandDetails` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|  
  
## <a name="remarks"></a>Comentarios  
 Los compiladores suelen proceden de un formato conocido como un compilador de dos pasos; en algunas versiones del compilador, cada paso se controla mediante un programa independiente. Se conocen como los compiladores de front-end y back-end, respectivamente, por lo tanto, las propiedades de símbolos para los números de versión de back-end y front-end.  
  
## <a name="see-also"></a>Vea también  
 [Operación de compilación](../../debugger/debug-interface-access/compiland.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)