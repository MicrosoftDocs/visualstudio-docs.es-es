---
title: IDiaLoadCallback2::RestrictDBGAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24317ff7a79815e5af2306b09cc8d2aa3bfdde0d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595858"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Determina si se permite la búsqueda de información de depuración desde archivos .dbg.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT RestrictDBGAccess();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Cualquier valor devuelto distinto `S_OK` para evitar que se busca información de depuración desde archivos .dbg.

## <a name="see-also"></a>Vea también
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)