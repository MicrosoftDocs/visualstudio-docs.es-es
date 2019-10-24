---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745416"
---
# <a name="compilanddetails"></a>CompilandDetails
La compilación de la información se divide entre símbolos con una `SymTagCompiland` etiqueta (bajo detalle) y una etiqueta `SymTagCompilandDetails` (alto detalle). `SymTagCompilandDetails` requiere la carga de símbolos adicionales. Sin embargo, proporciona una gran cantidad de información sobre la operación de compilación que no está disponible con un símbolo de `SymTagCompiland`.

## <a name="properties"></a>Propiedades
 En la tabla siguiente se muestran las propiedades que son válidas para este tipo de símbolo.

|Propiedad.|Tipo de datos|Descripción|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Número de compilación de back-end del compilador.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Número de versión principal de back-end del compilador.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versión secundaria de back-end del compilador.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nombre del compilador que generó esta operación de compilación (solo en el SDK de DIA V 8.0 o posterior).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` si editar y continuar se habilitó en la compilación.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilación de front-end del compilador.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Número de versión principal de front-end del compilador.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versión secundaria de front-end del compilador.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` si esta operación de compilación tiene información de depuración (solo en el SDK de DIA V 8.0 o posterior).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` si esta compilación contiene código administrado (solo en el SDK de DIA v 8.0 o posterior).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si la operación de compilación se compiló con el modificador de compilador [/GS (comprobación de seguridad del búfer)](/cpp/build/reference/gs-buffer-security-check) (solo en el SDK de dia v 8.0 o posterior).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` si la operación de compilación se convirtió del código de lenguaje intermedio común (CIL) en código nativo.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` si los tipos definidos por el usuario (UDT) se han alineado con algún límite de memoria especificado (solo en el SDK de DIA V 8.0 o posterior).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` si la operación de compilación se compiló con el modificador de compilador [/hotpatch (crear imagen una)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (solo en el SDK de dia v 8.0 o posterior).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` si la operación de compilación se compiló con el modificador de compilador [/LTCG (generación de código en tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) (solo en el SDK de dia v 8.0 o posterior).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si la operación de compilación es un módulo de lenguaje intermedio de Microsoft (MSIL) (solo en el SDK de DIA v 8.0 o posterior).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Lenguaje de código fuente.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|IDENTIFICADOR del símbolo primario léxico.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma en la que se compiló la compilación (uno de los valores de [enumeración CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|IDENTIFICADOR de índice del símbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagCompilandDetails` (uno de los valores de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Comentarios
 Los compiladores suelen tener un formato conocido como compilador de dos pasos; en algunas versiones de compilador, cada paso se controla mediante un programa independiente. Estos se conocen como compiladores front-end y back-end, respectivamente; por lo tanto, las propiedades de símbolos para los números de versión de back-end y front-end.

## <a name="see-also"></a>Vea también
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)