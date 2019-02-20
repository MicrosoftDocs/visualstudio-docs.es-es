---
title: NameSearchOptions | Microsoft Docs
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
ms.openlocfilehash: 8fa637a5f403a4651541d920c6390204ee579994
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318620"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Especifica las opciones de búsqueda para los nombres de archivo y símbolos.

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
`nsNone`  
No se especifican opciones.

`nsfCaseSensitive`  
Se aplica a una coincidencia de nombre distingue mayúsculas de minúsculas.

`nsfCaseInsensitive`  
Se aplica a una coincidencia de mayúsculas y minúsculas del nombre.

`nsfFNameExt`  
Trata los nombres como rutas de acceso y se aplica a la coincidencia de nombres nombreDeArchivo.ext.

`nsfRegularExpression`  
Se aplica a una coincidencia de mayúsculas y minúsculas del nombre con asteriscos (*) y signos de interrogación (?) como caracteres comodín.

`nsfUndecoratedName`  
Solo se aplica a los símbolos que tienen tanto no representativos y nombres representativos.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se pasan a los métodos siguientes:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisitos
Encabezado: dia2.h

## <a name="see-also"></a>Vea también
[Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
