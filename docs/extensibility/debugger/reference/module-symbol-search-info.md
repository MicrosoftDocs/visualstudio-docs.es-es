---
title: MODULE_SYMBOL_SEARCH_INFO de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714250"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene información de estado sobre las rutas de búsqueda de símbolos que se han buscado.

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

## <a name="members"></a>Miembros

`dwValidFields`\
Una combinación de indicadores de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica el tipo de información de búsqueda que se describe en esta estructura.

`bstrVerboseSearchInfo`\
Ruta de búsqueda y resultados concatenados en una sola cadena.

## <a name="remarks"></a>Observaciones

Esta estructura se devuelve de una llamada a la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método.

Si `bstrVerboseSearchInfo` el campo no está vacío, contiene una lista de rutas buscadas y los resultados de esa búsqueda. La lista tiene un formato con una ruta de acceso, seguida de puntos suspensivos ("..."), seguido del resultado. Si hay más de un par de resultados de ruta de acceso, cada par está separado por un par de "-r-n" (carriage-return/linefeed). El patrón tiene este aspecto:

\<camino>... \<> ruta de\<acceso de>>... \<resultado>>\<de ruta de acceso... \<resultado>

Tenga en cuenta que la última entrada no tiene una secuencia de la lista.

Aquí hay `bstrVerboseSearchInfo` una cadena posible que se ha enviado a estándar out.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
