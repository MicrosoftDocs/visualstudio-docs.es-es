---
description: Contiene información de estado sobre las rutas de acceso de búsqueda de símbolos que se han buscado.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc914334fc4b8ebf2dd73f691cdec242e19364a9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222294"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene información de estado sobre las rutas de acceso de búsqueda de símbolos que se han buscado.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Members

`dwValidFields`\
Combinación de marcas de la enumeración [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) que especifica el tipo de información de búsqueda que se describe en esta estructura.

`bstrVerboseSearchInfo`\
La ruta de búsqueda y los resultados se concatenan en una sola cadena.

## <a name="remarks"></a>Observaciones

Esta estructura se devuelve de una llamada al método [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .

Si el `bstrVerboseSearchInfo` campo no está vacío, contiene una lista de rutas de acceso de búsqueda y los resultados de esa búsqueda. Se da formato a la lista con una ruta de acceso, seguida de un botón de puntos suspensivos ("..."), seguido del resultado. Si hay más de un par de resultados de ruta de acceso, cada par está separado por un par "\r\n" (retorno de carro/avance de bits). El patrón tiene el siguiente aspecto:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Tenga en cuenta que la última entrada no tiene una secuencia \r\n.

Esta es una posible `bstrVerboseSearchInfo` cadena que se ha enviado a la salida estándar.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisitos

Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también

- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
