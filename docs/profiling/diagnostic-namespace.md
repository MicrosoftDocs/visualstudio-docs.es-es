---
title: diagnostic (espacio de nombres) | Microsoft Docs
description: Use el espacio de nombres diagnostic para emitir marcadores del visualizador de simultaneidad. El espacio de nombres diagnostic es un miembro del espacio de nombres de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224e375c1d1f463f1c07d41ca5a03efa5cabdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923738"
---
# <a name="diagnostic-namespace"></a>diagnostic (Espacio de nombres)
El espacio de nombres `diagnostics` proporciona funcionalidad para emitir los marcadores del visualizador de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
namespace diagnostic;
```

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|NOMBRE|Descripción|
|----------|-----------------|
|[marker_series (Clase)](../profiling/marker-series-class.md)|Representa un canal en serie de eventos generados por un único proveedor.|
|[span (Clase)](../profiling/span-class.md)|Define una fase de la aplicación.|

### <a name="enumerations"></a>Enumeraciones

|Nombre|Descripción|
|----------|-----------------|
|[marker_importance (Enumeración)](../profiling/marker-importance-enumeration.md)|Representa el nivel de importancia de un marcador del visualizador de simultaneidad.|

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: simultaneidad

## <a name="see-also"></a>Consulte también
- [Espacio de nombres de simultaneidad (Visualizador de simultaneidad)](../profiling/concurrency-namespace-concurrency-visualizer.md)