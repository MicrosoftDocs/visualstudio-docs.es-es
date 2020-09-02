---
title: CompilandDetails | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702999"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La información de compilación se divide entre símbolos con una `SymTagCompiland` etiqueta (detalle bajo) y una `SymTagCompilandDetails` etiqueta (alto detalle). `SymTagCompilandDetails` requiere la carga de símbolos adicionales. Sin embargo, proporciona una gran cantidad de información sobre la operación de compilación que no está disponible con un `SymTagCompiland` símbolo.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades que son válidas para este tipo de símbolo.  
  
|Propiedad|Tipo de datos|Descripción|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Número de compilación de back-end del compilador.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Número de versión principal de back-end del compilador.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versión secundaria de back-end del compilador.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nombre del compilador que generó esta operación de compilación (solo en el SDK de DIA V 8.0 o posterior).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Si editar y continuar se habilitó en la compilación.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilación de front-end del compilador.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Número de versión principal de front-end del compilador.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versión secundaria de front-end del compilador.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Si esta operación de compilación tiene información de depuración (solo en el SDK de DIA V 8.0 o posterior).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Si esta operación de compilación contiene código administrado (solo en el SDK de DIA v 8.0 o posterior).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con el modificador de compilador [/GS (comprobación de seguridad del búfer)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) (solo en el SDK de dia v 8.0 o posterior).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Si la operación de compilación se convirtió del código de lenguaje intermedio común (CIL) en código nativo.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Si los tipos definidos por el usuario (UDT) se han alineado con algún límite de memoria especificado (solo en el SDK de DIA V 8.0 o posterior).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Si la compilación se compiló con el modificador de compilador [/hotpatch (crear imagen una)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) (solo en el SDK de dia v 8.0 o posterior).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Si la operación de compilación se compiló con el modificador de compilador [/LTCG (generación de código en tiempo de vínculo)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) (solo en el SDK de dia v 8.0 o posterior).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si la operación de compilación es un módulo de lenguaje intermedio de Microsoft (MSIL) (solo en el SDK de DIA v 8.0 o posterior).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Lenguaje de código fuente.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|IDENTIFICADOR del símbolo primario léxico.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma en la que se compiló la compilación (uno de los valores de [enumeración CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|IDENTIFICADOR de índice del símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagCompilandDetails` (uno de los valores de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) ).|  
  
## <a name="remarks"></a>Observaciones  
 Los compiladores suelen tener un formato conocido como compilador de dos pasos; en algunas versiones de compilador, cada paso se controla mediante un programa independiente. Estos se conocen como compiladores front-end y back-end, respectivamente; por lo tanto, las propiedades de símbolos para los números de versión de back-end y front-end.  
  
## <a name="see-also"></a>Consulte también  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
