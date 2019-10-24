---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5a24a136bb9c04366449a91d825ddbecff2957
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740322"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Recupera una marca que indica si el símbolo corresponde al símbolo de *intervalo de definición* para el componente de etiqueta de una variable de puntero en el código C++ compilado para un acelerador de amp. El símbolo de intervalo de definición es la ubicación de una variable para un intervalo de direcciones.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parámetros
 `pFlag`

enuncia Un puntero a un `BOOL` que indica si el símbolo corresponde al símbolo de intervalo de definición.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)