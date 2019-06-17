---
title: IDiaSymbol::get_machineType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef0507ccb7036748f5c9d36c9de521a17860a39
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67032712"
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
Recupera el tipo de la CPU de destino.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_machineType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve un valor de la [IMAGE_FILE_MACHINE_ constantes](/windows/desktop/SysInfo/image-file-machine-constants) que especifica el tipo de CPU de destino.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="see-also"></a>Vea también
- [Constantes IMAGE_FILE_MACHINE_](/windows/desktop/SysInfo/image-file-machine-constants) 
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)