---
title: API de gráficos y estadísticas de memoria | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735572"
---
# <a name="graphics-api-and-memory-statistics"></a>API de gráficos y estadísticas de memoria
<!-- VERSIONLESS -->
Visual Studio 2017 y versiones posteriores admiten las estadísticas de la API de gráficos y las herramientas de estadísticas de memoria.  Estas dos herramientas permiten ver diversos bits de información sobre el uso de la API de Direct3D, así como el consumo de memoria de la GPU de varios recursos.

## <a name="graphics-api-statistics"></a>Estadísticas de API de gráficos
Las estadísticas de la API de gráficos de Visual Studio Diagnóstico de gráficos permiten ver todas las llamadas de Direct3D realizadas y el recuento de cada llamada.  Para ver la ventana, seleccione el elemento de menú **ver estadísticas de API de >** .

![Estadísticas de API](media/gfx_diag_api_statistics.png)

Esta herramienta puede resultar útil para detectar llamadas de DirectX que es posible que no se dé de baja, o que las llamadas que está realizando con demasiada frecuencia.

Puede hacer clic con el botón secundario en la ventana para copiar todos los datos como CSV, que se pueden pegar en algo como Excel para su posterior análisis.

## <a name="memory-statistics"></a>Estadísticas de memoria
Esta herramienta mostrará cuánta memoria asigna el controlador de gráficos para los recursos que crea en un marco.  Para ver esta ventana, seleccione el elemento de menú **ver estadísticas de memoria de >** .

![Estadísticas de memoria](media/gfx_diag_memory_statistics.png)

La columna **asignación de GPU** muestra la cantidad de memoria utilizada por el evento que se muestra en la columna **evento** .  También puede seleccionar el icono de inspección ![watch icono ](media/gfx_watch.png) para ver el [historial de recursos](graphics-event-list.md#resource-history) del evento seleccionado.

Al igual que con la herramienta API Statistics, puede hacer clic con el botón derecho en la ventana para copiar todos los datos como CSV, que se pueden pegar en algo como Excel para su posterior análisis.

## <a name="see-also"></a>Vea también
- [Diagnóstico de gráficos (Depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)
- [Historial de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->