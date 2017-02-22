---
title: "Vista Funciones: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
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
  - "Funciones (vista)"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Funciones: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista de informe Funciones de datos de contención muestra las funciones de la generación de perfiles que no se pudieron activar durante la ejecución.  
  
 En la tabla siguiente se explican los valores que se muestran en la vista Funciones de un archivo de datos de generación de perfiles que se recopiló utilizando el método de simultaneidad.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|La cantidad de tiempo durante el cual esta función no pudo ejecutar el código del cuerpo de la función.  No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|  
|**% de tiempo de bloqueo exclusivo**|El porcentaje de tiempo de bloqueo exclusivo de esta función con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones exclusivas**|El número de veces que esta función no pudo ejecutar código del cuerpo de la función.  No se incluyen las contenciones de las funciones a las que llamó la función.|  
|**% de contenciones exclusivas**|Porcentaje de las contenciones exclusivas de esta función con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Dirección de función**|Dirección de la función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Tiempo de bloqueo inclusivo**|El tiempo que esta función o una función a la que llamó esta función no se pudo ejecutar.|  
|**% de tiempo de bloqueo inclusivo**|El porcentaje de tiempo de bloqueo inclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|El número de veces que esta función o una función a la que llamó esta función no se pudo ejecutar.|  
|**% de contenciones inclusivas**|Porcentaje de contenciones inclusivas de esta función o módulo con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso en el que se estaba ejecutando la función.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Funciones](../profiling/functions-view.md)   
 [Vista de funciones \- Instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vista de funciones \- Muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vista Funciones](../profiling/functions-view-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)