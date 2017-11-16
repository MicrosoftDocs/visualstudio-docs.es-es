---
title: Vistas de datos de memoria de .NET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6bbbc764c7b5275082b6261249d48122ea3c836
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="net-memory-data-views"></a>Vistas de datos de memoria de .NET
Esta sección contiene información de referencia acerca de las vistas y los informes de archivos de datos del generador de perfiles que contienen datos de generación de perfiles de memoria de .NET.  
  
## <a name="in-this-section"></a>En esta sección  
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)  
 Enumera las funciones y los tipos que asignaron la mayor parte de la memoria.  
  
 [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md)  
 Enumera los tipos asignados en la generación de perfiles y los árboles de llamadas (rutas de acceso de ejecución) que produjeron la asignación del tipo.  
  
 [Vista Duración del objeto](../profiling/object-lifetime-view.md)  
 Enumera los tipos asignados en la generación de perfiles y el número de instancias, el tamaño en bytes y la generación de recolección de elementos no utilizados del tipo.  
  
 [Vista Árbol de llamadas: muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 Muestra un árbol de jerarquía que representa las rutas de acceso de ejecución y los datos de asignación de memoria de las funciones incluidas en la ejecución de generación de perfiles.  
  
 [Vista Módulos: muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 Organiza los datos de asignación de memoria de .NET por módulo y enumera las funciones, las líneas de código fuente y las instrucciones que se estaban ejecutando cuando se asignó la memoria.  
  
 [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 Enumera los datos de asignación de memoria de función seleccionada, de las funciones que llamaron a la función seleccionada y de las funciones a las que llamó la función seleccionada.  
  
 [Vista Funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 Enumera los datos de asignación de memoria de las funciones de la ejecución de generación de perfiles.  
  
 [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 Enumera los datos de asignación de memoria de las líneas de código fuente de las funciones de la ejecución de generación de perfiles.  
  
 [Vista Punteros de instrucciones (IP): muestreo](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 Enumera los datos de asignación de memoria de las instrucciones de las funciones de la ejecución de generación de perfiles.  
  
 [Vista Árbol de llamadas: instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 Muestra un árbol de jerarquía que representa las rutas de acceso de ejecución, los datos de asignación de memoria y los datos detallados de tiempo para las funciones instrumentadas de la ejecución de generación de perfiles.  
  
 [Vista Módulos: instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 Organiza los datos de generación de perfiles por módulo y enumera las funciones, los datos de asignación de perfiles y los datos detallados de tiempo del módulo.  
  
 [Vista Llamador y destinatario: datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 Enumera los datos de asignación de memoria e información detallada de tiempo para una función instrumentada seleccionada, para las funciones que llamaron a la función seleccionada y para las funciones a las que llamó la función seleccionada.  
  
 [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 Enumera los datos de asignación de memoria de las funciones instrumentadas de la ejecución de generación de perfiles.  
  
## <a name="reference"></a>Referencia  
 [Vista Detalles de la función](../profiling/function-details-view.md)  
 Muestra un gráfico de la relación entre una función seleccionada y las funciones que llamaron y fueron llamadas por dicha función.  
  
 [Vista Proceso](../profiling/process-view.md)  
 Muestra en una lista las horas de inicio y fin de procesos y subprocesos.  
  
 [Vista Marcas](../profiling/marks-view.md)  
 Enumera eventos de muestreo y ETW que se insertaron en un archivo de datos de generación de perfiles.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Vistas de datos del método de muestreo](../profiling/profiler-sampling-method-data-views.md)  
 Información de referencia para las vistas y los informes de archivos de datos del generador de perfiles generados mediante el método de muestreo.  
  
 [Vistas de datos del método de instrumentación](../profiling/instrumentation-method-data-views.md)  
 Información de referencia para las vistas y los informes de archivos de datos del generador de perfiles que se generaron mediante el método de instrumentación.