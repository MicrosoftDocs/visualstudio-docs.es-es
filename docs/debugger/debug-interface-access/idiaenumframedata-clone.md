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
ms.openlocfilehash: 47f6119eac1d48a7819f67bc57660c53e6b93b54
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744660"
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

enuncia Devuelve un objeto [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) que contiene un duplicado del enumerador. Los datos del marco no están duplicados, solo el enumerador.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)