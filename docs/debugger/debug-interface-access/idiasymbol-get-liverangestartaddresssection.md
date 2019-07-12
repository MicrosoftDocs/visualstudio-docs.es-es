---
title: IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99b5a14a321a28bdbe7337dcc7cdfa5febdad5d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786532"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Devuelve la parte de la sección de la dirección inicial del intervalo en el que el símbolo local es válido.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Parámetros
 `section`

[out] Devuelve la parte de la sección del intervalo de direcciones inicial.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

> [!NOTE]
> Un código de error devuelto significa que el símbolo no tiene información de rango en vivo.

## <a name="remarks"></a>Comentarios
 La dirección formada por la sección y el desplazamiento es el principio del intervalo en el que el símbolo es válido.

 Para obtener la parte de la dirección de desplazamiento, use [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2.h

 Biblioteca: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)