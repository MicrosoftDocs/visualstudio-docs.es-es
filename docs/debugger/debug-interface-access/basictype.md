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
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626120"
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
btNoType que se especifica ningún tipo básico.

es de tipo básico btVoid un `void`.

es de tipo básico btChar un `char` (tipo de C o C++).

btWChar tipo básico es un carácter de ancho (Unicode) (`WCHAR`).

es de tipo básico btInt `signed int` (tipo de C o C++).

es de tipo básico btUInt `unsigned int` (tipo de C o C++).

btFloat tipo básico es un número de punto flotante (`FLOAT`).

btBCD tipo básico es un decimal codificado en binario (`BCD`).

btBool tipo básico es un valor booleano (`BOOL`).

es de tipo básico btLong un `long int` (tipo de C o C++).

es de tipo básico btULong un `unsigned long int` (tipo de C o C++).

btCurrency tipo básico es la moneda.

btDate tipo básico es la fecha y hora (`DATE`).

btVariant tipo básico es una estructura de tipo de variable (`VARIANT`).

btComplex tipo básico es un número complejo.

btBit tipo básico es un poco.

btBSTR tipo básico es una cadena binaria o básica (`BSTR`).

es de tipo básico btHresult un `HRESULT`.

## <a name="remarks"></a>Comentarios
Devuelven los valores de esta enumeración la [Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
