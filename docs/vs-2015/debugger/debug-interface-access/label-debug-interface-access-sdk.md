---
title: Etiqueta (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f7d1721f8f48b8bcaaaba4c32a5ad323941d59c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682729"
---
# <a name="label-debug-interface-access-sdk"></a>Etiqueta (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una ubicación en el código del programa se identifica mediante un `SymTagLabel` símbolo.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades que son válidas para este tipo de símbolo.  
  
|Propiedad|Tipo de datos|Descripción|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte de desplazamiento de la ubicación; para obtener más información, consulte la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte de la sección de la ubicación; para obtener más información, consulte la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Si la etiqueta utiliza una Convención de llamada personalizada.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Si Label realiza una devolución Far.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Si la etiqueta contiene un valor devuelto de la interrupción.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la operación de compilación, bloque o función envolvente.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|IDENTIFICADOR del símbolo primario léxico.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Las etiquetas tienen ubicaciones estáticas; para obtener más información, vea la enumeración de [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md) .|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre de la etiqueta.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Si la etiqueta se especificó con el atributo [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) .|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Si la etiqueta se especificó con el atributo [Return](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) .|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Si nunca se llama a la etiqueta.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Desplazamiento del símbolo en la memoria; para obtener más información, consulte la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel` .|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Si el código tiene información de depuración para el código optimizado.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posición relativa de esta etiqueta dentro de su módulo.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|IDENTIFICADOR de índice del símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagFuncDebugLabel` (uno de los valores de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) ).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posición de esta etiqueta dentro de la imagen ejecutable.|  
  
## <a name="see-also"></a>Consulte también  
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)
