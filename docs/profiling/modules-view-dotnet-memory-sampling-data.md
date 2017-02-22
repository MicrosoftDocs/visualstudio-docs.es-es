---
title: "Vista M&#243;dulos: datos de muestreo de memoria de .NET del generador de perfiles | Microsoft Docs"
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
  - "Módulos (vista)"
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista M&#243;dulos: datos de muestreo de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Módulos de los datos de asignación de memoria de .NET recopilados mediante el método de muestreo agrupa los datos de memoria por los módulos que se ejecutaron en la generación de perfiles.  Cada módulo es la raíz de un árbol jerárquico.  Las funciones del módulo se enumeran bajo el nodo de módulo.  
  
 Los números de línea del archivo de origen de las instrucciones que asignan memoria se enumeran bajo el nodo de función y las direcciones de las instrucciones que realizan la asignación se enumeran bajo el nodo de línea.  Los valores inclusivos y exclusivos siempre son iguales en los datos de línea y de instrucción.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del módulo, función, número de línea o dirección de instrucción.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Asignaciones de inclusión**|-   En una función, el número total de objetos que creó la función.  El número incluye los objetos creados en las funciones de destinatario a las que llamó esta función.<br />-   En un módulo, el número de objetos de una ejecución de generación de perfiles que se asignaron cuando se estaba ejecutando al menos una función del módulo.  El número incluye los objetos creados en todas las funciones a las que llamaron las funciones del módulo.<br />-   En una línea o instrucción, el número total de objetos asignados por la línea o la instrucción.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos asignados durante la generación de perfiles que fueron objeto de asignaciones inclusivas del módulo, función, línea o instrucción.|  
|**Asignaciones de exclusión**|-   En la función actual, el número de objetos creados cuando la función estaba ejecutando código del cuerpo de la función \(es decir, cuando la función estaba en la parte superior de la pila de llamadas\).  El número no incluye los objetos creados en funciones a las que llamó esta función.<br />-   En un módulo, la suma de las asignaciones exclusivas de las funciones del módulo.<br />-   En una línea o instrucción, el número total de objetos creados por esta línea o la instrucción.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos asignados durante la generación de perfiles que fueron objeto de asignaciones exclusivas del módulo, función, línea o instrucción.|  
|**Bytes inclusivos**|-   En una función, el número total de bytes asignados por dicha función.  El número incluye los bytes asignados en las funciones a las que llamó esta función.<br />-   En un módulo, el número de bytes asignados en una ejecución de generación de perfiles que se asignaron cuando se estaba ejecutando al menos una función del módulo.  El número incluye los objetos creados en todas las funciones a las que llamaron las funciones del módulo.<br />-   En una línea o instrucción, el número total de objetos creados por la línea o la instrucción.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes asignados durante la generación de perfiles que eran bytes inclusivos del módulo, función, línea o instrucción.|  
|**Bytes exclusivos**|-   En una función, el número total de bytes asignados por dicha función.  El número no incluye los bytes asignados en funciones a las que llamó esta función.<br />-   En un módulo, la suma de los bytes exclusivos asignados por las funciones del módulo.<br />-   En una línea o instrucción, el número total de objetos asignados por esta línea o la instrucción.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes asignados durante la generación de perfiles que eran bytes exclusivos del módulo, función, línea o instrucción.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista de módulos \- Instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista Módulos](../profiling/modules-view-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)