---
title: Estadísticas de API de gráficos y Estadísticas de memoria | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735572"
---
# <a name="graphics-api-and-memory-statistics"></a>Estadísticas de API de gráficos y Estadísticas de memoria
<!-- VERSIONLESS -->
En Visual Studio 2017 y versiones posteriores se admiten las herramientas Estadísticas de API de gráficos y Estadísticas de memoria.  Estas dos herramientas permiten ver diversos bits de información sobre el uso de la API de Direct3D, así como el consumo de memoria de la GPU de varios recursos.

## <a name="graphics-api-statistics"></a>Estadísticas de API de gráficos
La herramienta Estadísticas de API de gráficos de Diagnóstico de gráficos de Visual Studio permite ver todas las llamadas de Direct3D realizadas y el recuento de cada llamada.  Para ver la ventana, seleccione el elemento de menú **Ver > Estadísticas de API**.

![Estadísticas de API](media/gfx_diag_api_statistics.png)

Esta herramienta puede ser útil para detectar llamadas de DirectX que tal vez no sepa que realiza o para detectar llamadas que efectúa con demasiada frecuencia.

Puede hacer clic con el botón derecho en la ventana para copiar todos los datos como CSV, que se pueden pegar en aplicaciones como Excel para su posterior análisis.

## <a name="memory-statistics"></a>Estadísticas de memoria
Esta herramienta mostrará cuánta memoria asigna el controlador de gráficos a los recursos que crea en un fotograma.  Para ver esta ventana, seleccione el elemento de menú **Ver > Estadísticas de memoria**.

![Estadísticas de memoria](media/gfx_diag_memory_statistics.png)

En la columna **Asignación de GPU** se indica la cantidad de memoria que utiliza el evento mostrado en la columna **Evento**.  También puede seleccionar el ![icono Inspección](media/gfx_watch.png) para ver el [historial de recursos](graphics-event-list.md#resource-history) del evento seleccionado.

Al igual que en la herramienta Estadísticas de API, puede hacer clic con el botón derecho en la ventana para copiar todos los datos como CSV, que se pueden pegar en aplicaciones como Excel para su posterior análisis.

## <a name="see-also"></a>Vea también
- [Diagnóstico de gráficos (Depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)
- [Historial de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->