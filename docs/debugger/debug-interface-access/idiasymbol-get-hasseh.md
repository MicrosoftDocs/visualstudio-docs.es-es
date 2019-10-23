---
title: IDiaSymbol::get_hasSEH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSEH method
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e96216b5e33031405df3b01a3f76412a544bb51
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740435"
---
# <a name="idiasymbolget_hasseh"></a>IDiaSymbol::get_hasSEH
Recupera una marca que especifica si la función contiene cualquier [control de excepciones estructurado (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) (por ejemplo, bloques _ _ try/\__except).

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_hasSEH(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parámetros
 `pFlag`

enuncia Devuelve `TRUE` si la función tiene algún bloque de control de excepciones estructurado; de lo contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o el código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v 8.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Control de excepciones estructurado (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp)