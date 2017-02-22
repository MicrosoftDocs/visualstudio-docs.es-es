---
title: "Vista de asignaciones de memoria de .NET | Microsoft Docs"
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
  - "vs.performance.view.allocation"
helpviewer_keywords: 
  - "Asignaciones (vista)"
  - "informes de rendimiento, Asignación (vista)"
  - "informes de herramientas de generación de perfiles, Asignación (vista)"
  - "herramientas de generación de perfiles, Asignación (vista)"
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de asignaciones de memoria de .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Asignaciones muestra los tipos que se crearon durante la generación de perfiles.  Cada tipo es el nodo raíz de un árbol de llamadas que muestra las rutas de acceso de ejecución de funciones que dieron como resultado las asignaciones del tipo.  
  
 Los datos de una fila de tipo muestran el número total de objetos del tipo creados durante la generación de perfiles y el número total de bytes asignados para los objetos de ese tipo.  Los valores inclusivos y exclusivos para un tipo son siempre los mismos.  
  
-   Los valores inclusivos corresponden a objetos creados en las instancias de la función y a sus funciones secundarias, que fueron invocados por la función primaria en el árbol de llamadas.  
  
-   Los valores exclusivos corresponden a objetos que fueron creados directamente por la función cuando fueron invocados por la función primaria.  No se incluyen los objetos creados en funciones secundarias.  
  
 Los datos de una función muestran el número de objetos creados y el número de bytes asignados para los objetos del tipo primario.  
  
## Resaltar la ruta de acceso activa de ejecución  
 Puede encontrar la ruta de acceso de ejecución del árbol de llamadas que creó la mayoría de los objetos del tipo primario.  
  
-   Para mostrar la ruta de acceso más activa, haga clic con el botón secundario en el tipo o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre del tipo asignado o de la función.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene el tipo o función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene el tipo o función.|  
|**Archivo de origen**|Archivo de código fuente que contiene la definición del tipo o función.|  
|**Número de línea de función**|Número de línea del inicio de esta función o definición de tipo en el archivo de código fuente.|  
|**Nivel**|Indica si los datos corresponden a un tipo o a una función.|  
|**Asignaciones de inclusión**|-   En el caso de una función, número total de objetos del tipo primario creados por la función.  Este número incluye los objetos creados en las funciones secundarias.<br />-   En el caso de un tipo, número total de las instancias de ese tipo que se crearon.|  
|**Porcentaje de asignaciones inclusivas**|-   En el caso de una función, porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones inclusivas del tipo primario por parte de la función.<br />-   En el caso de un tipo, porcentaje del número total de objetos creados durante la generación de perfiles que fueron instancias del tipo.|  
|**Asignaciones de exclusión**|-   En el caso de una función, número de objetos creados cuando la función se estaba ejecutando directamente en la parte superior de la pila de llamadas.  Este número no incluye los objetos creados en las funciones secundarias.<br />-   En el caso de un tipo, número total de las instancias de ese tipo que se crearon.|  
|**Porcentaje de asignaciones exclusivas**|-   En el caso de una función, porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones exclusivas del tipo primario por parte de la función.<br />-   En el caso de un tipo, porcentaje del número total de objetos creados durante la generación de perfiles que fueron instancias del tipo.|  
|**Bytes inclusivos**|-   En el caso de una función, número de bytes de memoria que fueron asignados por la función para los objetos del tipo primario.  Este número incluye la memoria que fue asignada por las funciones secundarias.<br />-   En el caso de un tipo, número total de bytes que se asignaron durante la generación de perfiles para las instancias del tipo.|  
|**Porcentaje de bytes inclusivos**|-   En el caso de una función, porcentaje de toda la memoria asignada durante la generación de perfiles que fue objeto de asignaciones inclusivas del tipo primario por parte de la función.<br />-   En el caso de un tipo, porcentaje de toda la memoria asignada durante la generación de perfiles que se asignó para las instancias del tipo.|  
|**Bytes exclusivos**|-   En el caso de una función, número de bytes de memoria que fueron asignados por la función para los objetos del tipo primario.  Este número no incluye la memoria que fue asignada por las funciones secundarias.<br />-   En el caso de un tipo, número total de bytes que se asignaron durante la generación de perfiles para las instancias del tipo.|  
|**Porcentaje de bytes exclusivos**|-   En el caso de una función, porcentaje de toda la memoria asignada durante la generación de perfiles que fue objeto de asignaciones exclusivas del tipo primario por parte de la función.<br />-   En el caso de un tipo, porcentaje de toda la memoria asignada durante la generación de perfiles que se asignó para las instancias del tipo.|