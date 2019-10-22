---
title: API de gráficos y estadísticas de memoria | Documentos de Microsoft
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
ms.openlocfilehash: 7810889d4af411477573c71aa694d797a90763f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896024"
---
# <a name="graphics-api-and-memory-statistics"></a>API de gráficos y estadísticas de memoria
<!-- VERSIONLESS -->
Visual Studio 2017 y mayor compatibilidad con las estadísticas de la API de gráficos y herramientas de estadísticas de memoria.  Ambas herramientas le permiten ver los distintos bits de información en uso de la API de Direct3D, así como el consumo de memoria GPU de diversos recursos.

## <a name="graphics-api-statistics"></a>Estadísticas de la API de gráficos
Las estadísticas de la API de gráficos en diagnóstico de gráficos de Visual Studio le permite ver todas las llamadas de Direct3D que se realizaron y el recuento de cada llamada.  Para ver la ventana, seleccione el **Vista > estadísticas de API** elemento de menú.

![Estadísticas de API](media/gfx_diag_api_statistics.png)

Esta herramienta puede ser útil para detectar llamadas de DirectX que tal vez no sepa que se va a realizar o llamadas que realiza con demasiada frecuencia.

Puede hacer clic en la ventana para copiar todos los datos como CSV, que se puede pegar en algo parecido a Excel para su posterior análisis.

## <a name="memory-statistics"></a>Estadísticas de memoria
Esta herramienta mostrará cuánta memoria está asignando el controlador de gráficos para los recursos se crea en un marco.  Para ver esta ventana, seleccione el **Vista > estadísticas de memoria** elemento de menú.

![Estadísticas de memoria](media/gfx_diag_memory_statistics.png)

El **GPU asignación** columna muestra la cantidad de memoria utilizada por el evento que se muestra en el **eventos** columna.  También puede seleccionar el icono de inspección ![icono inspección](media/gfx_watch.png) para ver el [historial de recursos](graphics-event-list.md#resource-history) del evento seleccionado.

Al igual que con la herramienta de estadísticas de API, hacer clic en la ventana para copiar todos los datos como CSV, que se puede pegar en algo parecido a Excel para su posterior análisis.

## <a name="see-also"></a>Vea también
- [Diagnóstico de gráficos (Depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)
- [Historial de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->