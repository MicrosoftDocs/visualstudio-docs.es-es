---
title: Namesearchoptions (| Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c2b06e8d89405b38afe2b740ce860a78bc46cc
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661810"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica las opciones de búsqueda para los nombres de símbolos y archivos.

## <a name="syntax"></a>Sintaxis

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Elementos
`nsNone` No se especifica ninguna opción.

`nsfCaseSensitive`Aplica una coincidencia de nombre que distingue entre mayúsculas y minúsculas.

`nsfCaseInsensitive`Aplica una coincidencia de nombre que no distingue mayúsculas de minúsculas.

`nsfFNameExt`Trata los nombres como rutas de acceso y aplica una coincidencia de nombre de archivo. ext.

`nsfRegularExpression`Aplica una coincidencia de nombres que distingue entre mayúsculas y minúsculas mediante asteriscos (*) y signos de interrogación (?) como caracteres comodín. (No se admiten otros caracteres comunes de expresiones regulares).

`nsfUndecoratedName`Solo se aplica a símbolos que tienen nombres no representativos y representativos.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se pasan a los métodos siguientes:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
