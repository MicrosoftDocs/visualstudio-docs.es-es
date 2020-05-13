---
title: marker_importance (Enumeración) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999970"
---
# <a name="marker_importance-enumeration"></a>Enumeración marker_importance
Representa el nivel de importancia de un marcador del visualizador de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
enum marker_importance;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|NOMBRE|Descripción|
|----------|-----------------|
|`critical_importance`|Especifica que el marcador tiene una importancia crítica.|
|`high_importance`|Especifica que el marcador tiene una importancia alta.|
|`low_importance`|Especifica que el marcador tiene una importancia baja.|
|`normal_importance`|Especifica que el marcador tiene una importancia normal.|

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Vea también
- [espacio de nombres de diagnóstico](../profiling/diagnostic-namespace.md)