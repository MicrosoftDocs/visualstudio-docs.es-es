---
description: Representa el nivel de importancia de un marcador del visualizador de simultaneidad.
title: marker_importance (Enumeración) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223945"
---
# <a name="marker_importance-enumeration"></a>Enumeración marker_importance
Representa el nivel de importancia de un marcador del visualizador de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
enum marker_importance;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|
|`high_importance`|Especifica que el marcador tiene una importancia alta.|
|`low_importance`|Especifica que el marcador tiene una importancia baja.|
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte también
- [espacio de nombres de diagnóstico](../profiling/diagnostic-namespace.md)
