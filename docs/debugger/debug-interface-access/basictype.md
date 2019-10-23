---
title: BasicType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745477"
---
# <a name="basictype"></a>BasicType
Especifica el tipo básico del símbolo.

## <a name="syntax"></a>Sintaxis

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elementos
btNoType no se ha especificado ningún tipo básico.

el tipo básico de btVoid es un `void`.

btChar Basic Type es un `char` (C/C++ Type).

btWChar Basic Type es un carácter ancho (Unicode) (`WCHAR`).

btInt Basic Type es `signed int` (C/C++ Type).

btUInt Basic Type es `unsigned int` (C/C++ Type).

btFloat Basic Type es un número de punto flotante (`FLOAT`).

btBCD Basic Type es un decimal con codificación binaria (`BCD`).

btBool Basic Type es un valor booleano (`BOOL`).

btLong Basic Type es un `long int` (C/C++ Type).

btULong Basic Type es un `unsigned long int` (C/C++ Type).

el tipo básico de btCurrency es Currency.

el tipo básico de btDate es fecha y hora (`DATE`).

btVariant Basic Type es una estructura de tipo variable (`VARIANT`).

el tipo básico de btComplex es un número complejo.

el tipo básico de btBit es un poco.

btBSTR Basic Type es una cadena básica o binaria (`BSTR`).

el tipo básico de btHresult es un `HRESULT`.

## <a name="remarks"></a>Comentarios
El método [IDiaSymbol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) devuelve los valores de esta enumeración.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
