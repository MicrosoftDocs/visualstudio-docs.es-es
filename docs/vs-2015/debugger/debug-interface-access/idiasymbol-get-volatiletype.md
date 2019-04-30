---
title: IDiaSymbol::get_volatileType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_volatileType method
ms.assetid: 19782a4d-40a8-467b-ab7d-58bc4d812309
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d36d688c29894bd65eae29e033ef1d94869e04fd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386578"
---
# <a name="idiasymbolgetvolatiletype"></a>IDiaSymbol::get_volatileType
Recupera una marca que especifica si el tipo de datos definido por el usuario (UDT) es volátil.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_volatileType ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve `TRUE` si el UDT es volátil; en caso contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 En C++, un UDT se puede marcar con el `volatile` palabra clave, que indica que su contenido no se supone que existe desde un acceso a la siguiente.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)