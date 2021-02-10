---
title: marker_series::is_enabled (Método) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e68ec76737308d9bc9478f4106420626389f5eeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917733"
---
# <a name="marker_seriesis_enabled-method"></a>Método marker_series::is_enabled
Determina si alguna sesión habilitó el proveedor.

## <a name="syntax"></a>Sintaxis

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>Parámetros
 `_Importance` Nivel de importancia.

 `_Category` Categoría.

## <a name="return-value"></a>Valor devuelto

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Vea también
- [Clase marker_series](../profiling/marker-series-class.md)