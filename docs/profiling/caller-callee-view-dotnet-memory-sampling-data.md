---
title: "Vista Llamador y destinatario: datos de muestreo de memoria de .NET del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Llamador y destinatario (vista)"
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Llamador y destinatario: datos de muestreo de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Llamador y destinatario muestra datos de generación de perfiles de memoria de .NET para una función seleccionada y sus funciones primarias y secundarias.  Contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central y presenta información de generación de perfiles de memoria acerca de la función seleccionada.  Los valores incluyen todas las llamadas muestreadas a la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior y presenta la cantidad del valor de la función seleccionada \(actual\) generado por llamadas de la función de llamador \(primaria\).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior y presenta datos de generación de perfiles de memoria para las funciones de destinatario \(secundarias\) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
 Haga doble clic en una fila de función de llamador o de destinatario para convertir esa fila en la función actual.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección de la función.|  
|**Tipo**|El contexto de la función:<br /><br /> **0** \- la función actual<br /><br /> **1** \- una función que llama a la función actual<br /><br /> **2** \- una función a la que llama la función actual<br /><br /> Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nivel**|Profundidad de la función en el árbol de llamadas.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Asignaciones de inclusión**|-   En la función actual, número de objetos que fueron asignados por la función en la ejecución de generación de perfiles.  Este número incluye los objetos creados en las funciones de destinatario.<br />-   En una función de llamador, el número de asignaciones inclusivas de la función actual generadas por llamadas desde esta función.<br />-   En una función de destinatario, el número de objetos asignados por las instancias de la función a las que llamó la función actual.  El número incluye asignaciones realizadas por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones inclusivas por parte de esta función.|  
|**Asignaciones de exclusión**|-   En la función actual, el número de objetos creados cuando la función estaba ejecutando código del cuerpo de la función \(es decir, cuando la función estaba en la parte superior de la pila de llamadas\).  El número no incluye los objetos creados en funciones a las que llamó la función.<br />-   En una función de llamador, el número de asignaciones exclusivas de la función actual generadas por llamadas desde esta función.<br />-   En una función de destinatario, el número de objetos creados por las instancias de la función a las que llamó la función actual.  El número no incluye los objetos creados por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones inclusivas por parte de esta función.|  
|**Bytes inclusivos**|-   En la función actual, número de bytes de memoria que fueron asignados por la función en la ejecución de generación de perfiles.  El número incluye la memoria asignada en las funciones a las que llamó esta función.<br />-   En una función de llamador, el número de bytes inclusivos de la función actual generados por llamadas de la función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de la función generadas por llamadas desde la función actual.  El número incluye los bytes asignados por las funciones a las que llamó la función de destinatario.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones inclusivas de esta función.|  
|**Bytes exclusivos**|-   En la función actual, número de bytes de memoria que fueron asignados por la función en la ejecución de generación de perfiles.  Este número no incluye la memoria asignada por funciones llamadas por la función actual.<br />-   En una función de llamador, el número de bytes exclusivos de la función actual generados por llamadas de la función de llamador.<br />-   En una función de destinatario, el número de bytes asignados por las instancias de la función generadas por llamadas desde la función actual.  El número no incluye los bytes asignados por funciones a las que llamó la función de destinatario.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones exclusivas de esta función.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Llamador y destinatario \- Instrumentación](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-sampling-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-instrumentation-data.md)