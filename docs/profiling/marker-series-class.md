---
title: marker_series (Clase) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575922"
---
# <a name="markerseries-class"></a>Clase marker_series
Representa un canal de la serie de eventos generados por un único proveedor.

## <a name="syntax"></a>Sintaxis

```cpp
class marker_series;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|nombre|Descripción|
|----------|-----------------|
|[Constructor marker_series::marker_series](../profiling/marker-series-marker-series-constructor.md)|Inicializa una nueva instancia de la clase `marker_series`.|
|[Destructor marker_series::~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Destruye el objeto marker_series y libera todos los recursos asignados.|

### <a name="public-methods"></a>Métodos públicos

|nombre|Descripción|
|----------|-----------------|
|[Método marker_series::is_enabled](../profiling/marker-series-is-enabled-method.md)|Determina si alguna sesión habilitó el proveedor.|
|[Método marker_series::write_alert](../profiling/marker-series-write-alert-method.md)|Escribe una alerta en el archivo de seguimiento del visualizador de simultaneidad.|
|[Método marker_series::write_flag](../profiling/marker-series-write-flag-method.md)|Escribe una marca en el archivo de seguimiento del visualizador de simultaneidad.|
|[Método marker_series::write_message](../profiling/marker-series-write-message-method.md)|Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia
 `marker_series`

## <a name="requirements"></a>Requisitos
 **Encabezado:** *cvmarkersobj.h*

 **Espacio de nombres**: Concurrency::diagnostic

## <a name="see-also"></a>Vea también
- [espacio de nombres de diagnóstico](../profiling/diagnostic-namespace.md)