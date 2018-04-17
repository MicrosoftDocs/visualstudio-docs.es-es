---
title: API de gráficos y estadísticas de memoria | Documentos de Microsoft
ms.custom: ''
ms.date: 03/02/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b57edb59984537638dd32b621406775087ba680e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="graphics-api-and-memory-statistics"></a>API de gráficos y estadísticas de memoria
<!-- VERSIONLESS -->
2017 de Visual Studio y mayor compatibilidad con las estadísticas de la API de gráficos y las herramientas de estadísticas de memoria.  Ambas herramientas le permiten ver varios bits de información en uso de la API de Direct3D, así como el consumo de memoria GPU de varios recursos.

## <a name="graphics-api-statistics"></a>Estadísticas de la API de gráficos
Las estadísticas de la API de gráficos de diagnóstico de gráficos de Visual Studio le permite ver todas las llamadas de Direct3D que se realizaron y el recuento de cada llamada.  Para ver la ventana, seleccione la **Vista > API estadísticas** elemento de menú.

![Estadísticas de API](media/gfx_diag_api_statistics.png)

Esta herramienta puede resultar útil en detectar llamadas de DirectX que no puede saber está realizando o llamadas que se realizan con demasiada frecuencia.

Puede hacer clic en la ventana para copiar todos los datos como CSV, que se puede pegar en algo parecido a Excel para su posterior análisis.

## <a name="memory-statistics"></a>Estadísticas de memoria
Esta herramienta mostrará la cantidad de memoria es asignar el controlador de gráficos de los recursos se crea en un marco.  Para ver esta ventana, seleccione la **Vista > estadísticas de memoria** elemento de menú.

![Estadísticas de memoria](media/gfx_diag_memory_statistics.png)

El **GPU asignación** columna muestra la cantidad de memoria utilizada por el evento que se muestra en el **eventos** columna.  También puede seleccionar el icono de inspección ![icono inspección](media/gfx_watch.png) para ver el [recursos historial](graphics-event-list.md#resource-history) del evento seleccionado.

Al igual que con la herramienta de estadísticas de API, puede hacer clic en la ventana para copiar todos los datos como CSV, que se puede pegar en algo parecido a Excel para su posterior análisis.

## <a name="see-also"></a>Vea también  
[Diagnóstico de gráficos (depurar gráficos de DirectX)](visual-studio-graphics-diagnostics.md)   
[Historial de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->