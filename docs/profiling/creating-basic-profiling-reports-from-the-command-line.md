---
title: "Creación de informes básicos de generación de perfiles desde la línea de comandos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8915f71d4dcb84a481c0223a64afbddf9b0c722a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Crear informes básicos de generación de perfiles desde la línea de comandos
En este tema se describen los comandos básicos de VSPerfReport que generan informes de valores separados por comas (.csv) a partir de un archivo .vsp o .vsps de datos de generación de perfiles. Para una descripción de todas las opciones de informes, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Comandos de informe  
 Utilice uno de los comandos siguientes para crear un informe para un archivo de datos de generación de perfiles especificado.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Genera todos los informes disponibles para el archivo .vsp o .vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Genera los tipos de informe especificados.  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 Genera un informe que enumera cada evento de recolección de datos. Solamente en instrumentación.  
  
## <a name="summary-report-type-parameters"></a>Parámetros de resumen de tipo de informe  
 En la tabla siguiente se describen los informes que se generan con la opción de tipo de informe especificada. Las columnas de un informe dependen del método de generación de perfiles utilizado para recopilar los datos.  
  
|Parámetro de resumen|Descripción del informe|Referencia del informe|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Representa las relaciones de elemento primario/secundario entre funciones.|-   [Datos de muestreo](../profiling/caller-callee-view-sampling-data.md)<br />-   [Datos de instrumentación](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Datos de contención](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Enumera los datos de generación de perfiles por función.|-   [Datos de muestreo](../profiling/functions-view-sampling-data.md)<br />-   [Datos de instrumentación](../profiling/functions-view-instrumentation-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Datos de instrumentación de memoria de .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Datos de contención](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Representa las rutas de acceso de ejecución y los datos de generación de perfiles de las funciones incluidas en la ejecución de generación de perfiles.|-   [Datos de instrumentación](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Datos de muestreo](../profiling/call-tree-view-sampling-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Datos de instrumentación de memoria de .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Datos de contención](../profiling/call-tree-view-contention-data.md)|  
|**Contador**|Enumera las marcas de generación de perfiles y los valores de contador de rendimiento de Windows que se recopilaron durante la ejecución de generación de perfiles.|-   [Vista Marcas](../profiling/marks-view.md)|  
|**Ip**|Enumera los datos de generación de perfiles por instrucción.|-   [Datos de muestreo](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Datos de contención](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Enumera la duración de los objetos asignados.|-   [Vista Duración del objeto](../profiling/object-lifetime-view.md)|  
|**Line**|Enumera los datos de generación de perfiles por línea del código fuente.|-   [Datos de muestreo](../profiling/lines-view-sampling-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Datos de contención](../profiling/lines-view-contention-data.md)|  
|**Header**|Información de encabezado del archivo de datos de generación de perfiles.|Específica del archivo.|  
|**Marca**|Marcas de generación de perfiles recopiladas en la ejecución de generación de perfiles.|-   [Vista Marcas](../profiling/marks-view.md)|  
|**Módulo**|Enumera los datos de generación de perfiles de los módulos.|-   [Datos de muestreo](../profiling/modules-view-sampling-data.md)<br />-   [Datos de instrumentación](../profiling/modules-view-instrumentation-data.md)<br />-   [Datos de muestreo de memoria de .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Datos de instrumentación de memoria de .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Datos de contención](../profiling/modules-view-contention-data.md)|  
|**Process**|Enumera los datos de generación de perfiles de los procesos.|-   [Vista Proceso](../profiling/process-view.md)<br />-   [Datos de contención](../profiling/process-view-contention-data.md)|  
|**Subproceso**|Enumera los datos de generación de perfiles de los subprocesos.|-   [Vista Proceso](../profiling/process-view.md)|  
|**Type**|Enumera los datos de asignación de la generación de perfiles por tipo.|-   [Vista Asignaciones](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Contenciones de recursos.|-   [Contenciones de recursos](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Enumera los problemas de las reglas de rendimiento.|- Enumera el identificador de comprobación, la descripción y la ubicación en el código fuente del problema de la regla.|  
|**ETW**|Enumera todos los eventos de Seguimiento de eventos para Windows (ETW) recopilados en la generación de perfiles.|-   [Informe de ETW](../profiling/event-tracing-for-windows-etw-report.md)|