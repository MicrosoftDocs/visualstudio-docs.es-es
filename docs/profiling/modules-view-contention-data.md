---
title: "Vista M&#243;dulos: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
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
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista M&#243;dulos: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Módulos de los datos de contención muestra datos de simultaneidad agrupados por los módulos muestreados en los datos de generación de perfiles.  Cada módulo es la raíz de un árbol jerárquico.  Bajo el nodo de módulo se muestra las funciones del módulo donde se han producido eventos de contención.  
  
 Si la función estaba ejecutando su propio código cuando se produjo un evento de contención, es decir, si la función estaba en la parte superior de la pila de llamadas, bajo el nodo de la función se muestran las líneas de código fuente y las direcciones de instrucción que se estaban ejecutando.  Dado que los datos de una línea de código fuente o un puntero de instrucción se recopilan cuando se está ejecutando la línea o la instrucción, los valores inclusivo y exclusivo siempre son los mismos para los datos de línea y de instrucción.  
  
 En la tabla siguiente se describen los valores de las columnas de la vista Módulos de los datos de contención.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|-   En una función, el tiempo que esta función no pudo ejecutar código del cuerpo de la función.  No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.<br />-   En un módulo, la suma del tiempo de bloqueo exclusivo de las funciones del módulo.<br />-   En una línea o una instrucción, el tiempo durante el cual esta línea o instrucción no se pudo ejecutar.|  
|**% de tiempo de bloqueo exclusivo**|-   En una función o un módulo, el porcentaje de tiempo de bloqueo exclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de tiempo durante el cual esta línea o instrucción no se pudo ejecutar con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones exclusivas**|-   En una función, el número de veces que esta función no pudo ejecutar código del cuerpo de la función.  No se incluyen las contenciones de las funciones a las que llamó la función.<br />-   En un módulo, la suma de las contenciones exclusivas de las funciones del módulo.<br />-   En una línea o una instrucción, el número de veces que esta línea o instrucción no se pudo ejecutar.|  
|**% de contenciones exclusivas**|-   En una función o un módulo, el porcentaje de contenciones exclusivas de esta función o módulo con respecto a todas las contenciones de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de contenciones que impidieron la ejecución de esta línea o instrucción con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Tiempo de bloqueo inclusivo**|-   En una función, el tiempo que esta función o una función a la que llamó esta función no se pudo ejecutar.<br />-   En un módulo, la suma del tiempo de bloqueo en que al menos una función de este módulo estaba en la pila.<br />-   En una línea o una instrucción, el tiempo durante el cual esta línea o instrucción no se pudo ejecutar.|  
|**% de tiempo de bloqueo inclusivo**|-   En una función o un módulo, el porcentaje de tiempo de bloqueo inclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de tiempo durante el cual esta línea o instrucción no se pudo ejecutar con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|-   En una función, el número de veces que esta función o una función a la que llamó esta función no se pudo ejecutar.<br />-   En un módulo, el número de contenciones en que al menos una función de este módulo estaba en la pila.<br />-   En una línea o una instrucción, el número de veces que esta línea o instrucción no se pudo ejecutar.|  
|**% de contenciones inclusivas**|-   En una función o un módulo, el porcentaje de contenciones inclusivas de esta función o módulo con respecto a todas las contenciones de la ejecución de generación de perfiles.<br />-   En una línea o una instrucción, el porcentaje de tiempo durante el cual esta línea o instrucción no se pudo ejecutar con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función, línea o puntero de instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función, línea o puntero de instrucción.|  
|**Name**|Nombre de la función o el módulo.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Módulos](../profiling/modules-view.md)   
 [Vista de módulos \- Instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista de módulos \- Muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Vista Módulos](../profiling/modules-view-sampling-data.md)