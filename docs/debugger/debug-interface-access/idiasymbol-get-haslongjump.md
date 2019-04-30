---
title: IDiaSymbol::get_hasLongJump | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70036cd8add5c9c72262f29ba92fa6c7eaf8977d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401521"
---
# <a name="idiasymbolgethaslongjump"></a>IDiaSymbol::get_hasLongJump
Recupera una marca que especifica si la función contiene un uso de la [longjmp](/cpp/c-runtime-library/reference/longjmp) comando (emparejado con un [setjmp](/cpp/c-runtime-library/reference/setjmp) comando, forman el método de estilo C de control de excepciones).

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parámetros
 `pFlag`

[out] Devuelve `TRUE` si la función contiene un `longjmp` comando; de lo contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v8.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)