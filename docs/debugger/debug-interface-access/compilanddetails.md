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
ms.openlocfilehash: 896832ac3e96e499aa564d5bce44dc06185090de
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609233"
---
# <a name="compilanddetails"></a>CompilandDetails
Información de la operación de compilación se divide entre los símbolos con un `SymTagCompiland` etiqueta (detalle baja) y un `SymTagCompilandDetails` etiqueta (detalle alto). `SymTagCompilandDetails` requiere la carga de símbolos adicionales. Sin embargo, ofrece una gran cantidad de información sobre la operación de compilación que no está disponible con un `SymTagCompiland` símbolos.

## <a name="properties"></a>Propiedades
 En la tabla siguiente muestra las propiedades que son válidas para este tipo de símbolo.

|Propiedad.|Tipo de datos|Descripción|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Número de compilación de back-end del compilador.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Número de versión principal de back-end del compilador.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versión secundaria de back-end del compilador.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nombre del compilador que generó esta operación de compilación (solo en la versión V8.0 del SDK de DIA o posterior).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Si Editar y continuar se han habilitado en la compilación.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilación de front-end del compilador.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Número de versión principal front-end del compilador.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versión secundaria front-end del compilador.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Si esta operación de compilación tiene información de depuración (solo en la versión V8.0 del SDK de DIA o posterior).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Si esta operación de compilación contiene código administrado (solo en el SDK de DIA v8.0 o versiones posteriores).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/GS (comprobación de seguridad del búfer)](/cpp/build/reference/gs-buffer-security-check) modificador del compilador (solo en la versión V8.0 del SDK de DIA o posterior).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Si la operación de compilación se convirtió desde el código de Common Intermediate Language (CIL) en código nativo.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Si los tipos definidos por el usuario (UDT) se han asociado a algunos especifican límites de memoria (solo en la versión V8.0 del SDK de DIA o posterior).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/hotpatch (crear una imagen)](/cpp/build/reference/hotpatch-create-hotpatchable-image) modificador del compilador (solo en el SDK de DIA v8.0 o versiones posteriores).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con la [/LTCG (generación de código de tiempo de vínculo)](/cpp/build/reference/ltcg-link-time-code-generation) modificador del compilador (solo en la versión V8.0 del SDK de DIA o posterior).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si la operación de compilación es un módulo de lenguaje intermedio de Microsoft (MSIL) (sólo en el SDK de DIA v8.0 o versiones posteriores).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Lenguaje de código fuente.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Id. del símbolo léxico primario.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma en la que se compiló la operación de compilación (uno de los [CV_CPU_TYPE_e (enumeración)](../../debugger/debug-interface-access/cv-cpu-type-e.md) valores).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagCompilandDetails` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|

## <a name="remarks"></a>Comentarios
 Los compiladores suelen presentan en un formato conocido como un compilador de dos pasos; en algunas versiones del compilador, cada fase se controla mediante un programa independiente. Estos se conocen como los compiladores de front-end y back-end, respectivamente, por lo tanto, las propiedades de símbolos para los números de versión de back-end y front-end.

## <a name="see-also"></a>Vea también
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)