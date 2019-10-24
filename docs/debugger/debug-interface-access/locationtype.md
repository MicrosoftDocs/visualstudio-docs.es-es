---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738649"
---
# <a name="locationtype"></a>LocationType
Indica el tipo de información de ubicación contenida en un símbolo.

## <a name="syntax"></a>Sintaxis

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elementos
`LocIsNull` la información de ubicación no está disponible.

`LocIsStatic` ubicación es estática.

`LocIsTLS` ubicación está en el almacenamiento local del subproceso.

`LocIsRegRel` ubicación es el registro relativo.

`LocIsThisRel` ubicación `this` relativa.

`LocIsEnregistered` ubicación se encuentra en un registro.

`LocIsBitField` ubicación se encuentra en un campo de bits.

`LocIsSlot` ubicación es una ranura del lenguaje intermedio de Microsoft (MSIL).

`LocIsIlRel` ubicación es relativa a MSIL.

`LocInMetaData` ubicación está en los metadatos.

`LocIsConstant` ubicación se encuentra en un valor constante.

`LocTypeMax` el número de tipos de ubicación en esta enumeración.

## <a name="remarks"></a>Comentarios
Las propiedades disponibles para la interfaz [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dependen de la ubicación del símbolo en el archivo de imagen. Para obtener más información, vea [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).

Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)
