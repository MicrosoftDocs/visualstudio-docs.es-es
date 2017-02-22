---
title: "Vista de contenci&#243;n de recursos: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcecontention"
helpviewer_keywords: 
  - "vista de contención de recursos"
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de contenci&#243;n de recursos: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Contención de recursos muestra los datos de contención de los recursos origen de eventos de contención.  Un evento de contención se produce cuando una función de un subproceso se ve obligada a esperar para tener acceso al recurso porque una función de otro subproceso ha adquirido acceso exclusivo al recurso.  Cada recurso es el nodo raíz de un árbol de llamadas que muestra las rutas de acceso de ejecución de funciones que dieron como resultado los eventos de contención.  
  
## Valores de datos  
  
### Valores de recurso  
 Los datos de una fila de recurso muestran el tiempo total en que el acceso al recurso estuvo bloqueado en los datos de generación de perfiles y el número total de eventos de contención que se produjeron debido al conflicto de acceso a este recurso.  Los valores inclusivos y exclusivos para un recurso son siempre los mismos.  
  
### Valores de función  
 Los valores de función se basan en las instancias de la función que se produjeron en la ruta de acceso de ejecución representada en el árbol de llamadas.  
  
-   Los valores exclusivos se basan en los eventos que se produjeron cuando la función estaba ejecutando las instrucciones de su cuerpo de función.  En los valores exclusivos no se incluyen los eventos que se produjeron en funciones a las que llamó la función.  
  
-   Los valores inclusivos se basan en los eventos que se produjeron cuando se estaba ejecutando la función o una función a la que llamó la función.  
  
### Valores de porcentaje  
 Los valores de porcentaje se basan en el tiempo total o los eventos de contención de los datos de generación de perfiles.  Si se filtra el informe o vista de la ejecución de generación de perfiles, solamente se usan como valor total el tiempo de bloqueo y las contenciones de los datos filtrados.  
  
## Navegar en la vista Asignación de recursos  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del recurso o la función.|  
|**Tiempo de bloqueo exclusivo**|-   En un recurso, el tiempo total que estuvo bloqueado el acceso al recurso y que produjo la espera de un subproceso.<br />-   En una función, el tiempo que estas instancias de la función no pudieron tener acceso al recurso primario cuando la función estaba ejecutando código del cuerpo de la función.  No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|  
|**% de tiempo de bloqueo exclusivo**|-   En un recurso, el porcentaje de tiempo de bloqueo de este recurso con respecto al tiempo de bloqueo total de los datos de generación de perfiles.<br />-   En una función, el porcentaje de tiempo de bloqueo exclusivo de estas instancias de función con respecto al tiempo de bloqueo total de los datos de generación de perfiles.|  
|**Contenciones exclusivas**|-   En un recurso, el número total de veces que estuvo bloqueado el acceso al recurso y que produjo la espera de un subproceso.<br />-   En una función, el número de veces que estas instancias de la función no pudieron tener acceso al recurso primario cuando la función estaba ejecutando código del cuerpo de la función.  No se incluyen los eventos de bloqueo en funciones a las que llamó la función.|  
|**% de contenciones exclusivas**|-   En un recurso, el porcentaje de eventos de contención para el acceso a este recurso con respecto a todos los eventos de contención de los datos de generación de perfiles.<br />-   En una función, el porcentaje de eventos de contención exclusivos de estas instancias de función del recurso primario con respecto a todos los eventos de contención de los datos de generación de perfiles.|  
|**Tiempo de bloqueo inclusivo**|-   En un recurso, el tiempo total que estuvo bloqueado el acceso al recurso y que produjo la espera de un subproceso.<br />-   En una función, el tiempo que estas instancias de la función o de cualquier función a la que llamaron las instancias no pudieron tener acceso al recurso primario cuando la función estaba ejecutando código del cuerpo de la función.|  
|**% de tiempo de bloqueo inclusivo**|-   En un recurso, el porcentaje de tiempo de bloqueo de este recurso con respecto al tiempo de bloqueo total de los datos de generación de perfiles.<br />-   En una función, el porcentaje de tiempo de bloqueo inclusivo de estas instancias de función con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|-   En un recurso, el número total de veces que estuvo bloqueado el acceso al recurso y que produjo la espera de un subproceso.<br />-   En una función, el porcentaje de eventos de contención inclusivos de estas instancias de función del recurso primario con respecto a todos los eventos de contención de la ejecución de generación de perfiles.|  
|**% de contenciones inclusivas**|-   En un recurso, el porcentaje de eventos de contención para el acceso a este recurso con respecto a todos los eventos de contención de la ejecución de generación de perfiles.<br />-   En una función, el número de veces que estas instancias de la función no pudieron tener acceso al recurso primario cuando la función estaba ejecutando código del cuerpo de la función.  No se incluyen los eventos de bloqueo en funciones a las que llamó la función.|  
|**Nivel**|Profundidad de esta función en el árbol de llamadas.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso en el que se estaba ejecutando la función.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|