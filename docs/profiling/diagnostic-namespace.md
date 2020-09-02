---
title: diagnostic (espacio de nombres) | Microsoft Docs
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
ms.openlocfilehash: 680d304a8e4d21365d82f654265ae2f34582b636
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330260"
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
|[Clase marker_series](../profiling/marker-series-class.md)|Representa un canal de la serie de eventos generados por un único proveedor.|
|[Clase span](../profiling/span-class.md)|Define una fase de la aplicación.|

### <a name="enumerations"></a>Enumeraciones

|NOMBRE|Descripción|
|----------|-----------------|
|[Enumeración marker_importance](../profiling/marker-importance-enumeration.md)|Representa el nivel de importancia de un marcador del visualizador de simultaneidad.|

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: simultaneidad

## <a name="see-also"></a>Vea también
- [Espacio de nombres de simultaneidad (Visualizador de simultaneidad)](../profiling/concurrency-namespace-concurrency-visualizer.md)