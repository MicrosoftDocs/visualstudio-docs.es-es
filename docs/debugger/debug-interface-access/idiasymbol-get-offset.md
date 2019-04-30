---
title: IDiaSymbol::get_offset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0016ca267b3eaf2535896aab1ee58a470a192c9a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399451"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
Recupera el desplazamiento de la posición del símbolo. Cuando utilice el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md) es `LocIsRegRel` o `LocIsBitField`.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve el desplazamiento en bytes de la posición del símbolo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 El desplazamiento es desde algún punto conocido determinado previamente. Por ejemplo, el desplazamiento para un `LocIsBitField` tipo de ubicación es normalmente desde el principio de la clase contenedora.

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v7.0|

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)