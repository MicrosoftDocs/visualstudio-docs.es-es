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
ms.openlocfilehash: faff61833cb130902efbd64d60a16f74c507a3e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834135"
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
`LocIsNull` Información de ubicación no está disponible.

`LocIsStatic` Ubicación es estática.

`LocIsTLS` Ubicación está en almacenamiento local de subprocesos.

`LocIsRegRel` Ubicación es relativa del registro.

`LocIsThisRel` Ubicación es `this`-relativa.

`LocIsEnregistered` Ubicación está en un registro.

`LocIsBitField` Ubicación está en un campo de bits.

`LocIsSlot` La ubicación es una ranura de lenguaje intermedio de Microsoft (MSIL).

`LocIsIlRel` Ubicación es relativa a MSIL.

`LocInMetaData` Ubicación está en los metadatos.

`LocIsConstant` Ubicación está en un valor constante.

`LocTypeMax` El número de tipos de ubicación de esta enumeración.

## <a name="remarks"></a>Comentarios
Las propiedades disponibles para el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interfaz dependen de la ubicación del símbolo en el archivo de imagen. Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).

Los valores de esta enumeración se devuelven mediante una llamada a la [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)
