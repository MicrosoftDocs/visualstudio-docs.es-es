---
description: Determina si alguna sesión habilitó el proveedor.
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
ms.openlocfilehash: 0ce01d71b3fac63062a3f823f1862fd199fa39be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223581"
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

 **Espacio de nombres:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte también
- [Clase marker_series](../profiling/marker-series-class.md)
