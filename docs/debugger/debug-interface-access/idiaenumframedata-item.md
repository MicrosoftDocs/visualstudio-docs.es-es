---
title: IDiaEnumFrameData::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744613"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Recupera un elemento de datos de marco por medio de un índice.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Parámetros
 índice

de Índice del objeto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que se va a recuperar. El índice está en el intervalo de 0 a `count`-1, donde el método [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) devuelve `count`.

 section

enuncia Devuelve un objeto [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa el elemento de datos de marco deseado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)