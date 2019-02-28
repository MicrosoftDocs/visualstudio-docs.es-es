---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06ef9eb5969b351d49212e9b940988e7ff14c40e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636182"
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Devuelve la parte del ajuste de la dirección inicial del intervalo en el que el símbolo local es válido.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parámetros
 `offset`

[out] Devuelve la parte de desplazamiento del intervalo de direcciones inicial.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

> [!NOTE]
>  Un código de error devuelto significa que el símbolo no tiene información de rango en vivo.

## <a name="remarks"></a>Comentarios
 La dirección formada por la sección y el desplazamiento es el principio del intervalo en el que el símbolo es válido.

 Para obtener la parte de la sección de la dirección, use [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2.h

 Biblioteca: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)