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
ms.openlocfilehash: 020d631405586227d91fd06fb1794ab5554d1075
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226916"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
Recupera una marca que especifica si la función es una función virtual de presentación.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
`pRetVal`  
[out] Devuelve `TRUE` en caso contrario, devuelve si la función es virtual; Introducción `FALSE`.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o código de error.

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

Ambos `A::f1` y `B::f1` son funciones virtuales, pero `A::f1` es virtual Introducción.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v7.0|

## <a name="see-also"></a>Vea también
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
