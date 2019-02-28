---
title: IDiaEnumFrameData::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5c86d9f4f8eb02b0389e7ea28b5858f8576f6c6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598432"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parámetros
 ppenum

[out] Devuelve un [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) objeto que contiene un duplicado del enumerador. El marco de datos no se duplican, solo el enumerador.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)