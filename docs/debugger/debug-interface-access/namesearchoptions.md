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
ms.openlocfilehash: 61905c0c6c40d893cc8723b711d67690133a7155
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738613"
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

`nsfCaseSensitive` aplica una coincidencia de nombres que distingue entre mayúsculas y minúsculas.

`nsfCaseInsensitive` aplica una coincidencia de nombres que no distinguen mayúsculas de minúsculas.

`nsfFNameExt` trata los nombres como rutas de acceso y aplica una coincidencia de nombre de archivo. ext.

`nsfRegularExpression` aplica una coincidencia de nombres que distingue entre mayúsculas y minúsculas mediante asteriscos (*) y signos de interrogación (?) como caracteres comodín. (No se admiten otros caracteres comunes de expresiones regulares).

`nsfUndecoratedName` solo se aplica a símbolos que tienen nombres no representativos y representativos.

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
