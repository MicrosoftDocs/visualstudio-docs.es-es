---
title: IDiaEnumSourceFiles::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get_Count method
ms.assetid: 04083b97-e1ac-4baf-bf5a-50a4dc1c6f27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03d3d52706d549ce6dff4d30b9552ff5d35f379a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833381"
---
# <a name="idiaenumsourcefilesgetcount"></a>IDiaEnumSourceFiles::get_Count
Recupera el número de archivos de origen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 pRetVal

[out] Devuelve el número de archivos de origen.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)