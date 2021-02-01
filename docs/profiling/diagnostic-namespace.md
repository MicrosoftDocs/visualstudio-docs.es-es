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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686550"
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