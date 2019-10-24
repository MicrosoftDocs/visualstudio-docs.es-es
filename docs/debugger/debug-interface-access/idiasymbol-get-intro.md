---
title: IDiaSymbol::get_intro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740347"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Recupera una marca que especifica si la función es una función virtual de introducción.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
`pRetVal`

enuncia Devuelve `TRUE` si la función es de introducción virtual; de lo contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o el código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="example"></a>Ejemplo

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

Tanto `A::f1` como `B::f1` son funciones virtuales, pero `A::f1` es introductoria virtual.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v 7.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
