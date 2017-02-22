---
title: "Vista &#193;rbol de llamadas: Datos de instrumentaci&#243;n de memoria .NET del generador de perfiles | Microsoft Docs"
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
  - "Árbol de llamadas (vista)"
ms.assetid: dd359707-245a-4a36-8305-2e980b9edd53
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista &#193;rbol de llamadas: Datos de instrumentaci&#243;n de memoria .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Árbol de llamadas de datos de generación de perfiles de asignación de memoria .NET recopilados mediante el método de instrumentación muestra las rutas de acceso de ejecución de función que se recorrieron en la aplicación para la que se generaron perfiles.  La raíz del árbol es el punto de entrada a la aplicación o el componente.  Cada nodo de función enumera todas las funciones a las que llamó, así como los datos de control de tiempo y de memoria .NET para la función.  
  
 Los valores de la vista Árbol de llamadas son para las instancias de la función a las que llamó la función principal en el árbol de llamadas.  Los valores de porcentaje se calculan comparando el valor de instancia de función con el número total o el tamaño de las asignaciones en la ejecución de asignación de perfiles.  
  
## Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas se puede expandir y puede resaltar la ruta de acceso de ejecución del proceso o la función que creó el mayor objeto de memoria o el mayor número de objetos de memoria.  Para mostrar la ruta de acceso más activa, haga clic con el botón secundario del mouse en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## Establecer el nodo raíz del árbol de llamadas  
 Cada uno de los procesos de la generación de perfiles se muestra como nodo raíz.  Para establecer el nodo de inicio de la vista Árbol de llamadas, haga clic con el botón secundario del mouse en el nodo que desee establecer como nodo de inicio y, a continuación, seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado.  Puede restablecer el nodo raíz en el nodo que estaba viendo; haga clic con el botón secundario del mouse en la ventana Vista Árbol de llamadas y seleccione **Restablecer raíz**.  
  
## General  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Nombre de la función**|Nombre de la función.|  
|**Dirección de función**|Dirección de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Número de llamadas**|Número total de llamadas realizadas a la función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|El nombre que se asigna al proceso.|  
|**Tiempo de sobrecarga del análisis de exclusión**|Sobrecarga de tiempo para esta función debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos exclusivos.|  
|**Tiempo de sobrecarga del análisis de inclusión**|Sobrecarga de tiempo para esta función y sus funciones secundarias debida a la instrumentación.  La sobrecarga por sondeos se ha restado de todos los tiempos inclusivos.|  
|**Tipo**|El contexto de la función:<br /><br /> -   **0**: la función actual<br />-   **1**: una función que llama a la función actual<br />-   **2**: una función a la que llama la función actual<br /><br /> Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nombre de la función raíz**|El nombre de la función actual.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valores de memoria .NET  
 Los valores de memoria de .NET inclusivos de una función indican el número \(asignaciones\) y tamaño \(bytes\) de los objetos creados por la función y las funciones que fueron llamadas por la función.  
  
 Los valores de memoria exclusivos indican el número y tamaño de los objetos que fueron creados por código en el cuerpo de la función y no por funciones a las que llamó la función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Asignaciones de inclusión**|El número de objetos asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron asignaciones inclusivas de las instancias de la función llamadas por la función principal en el árbol de llamadas.|  
|**Asignaciones de exclusión**|El número de objetos asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número no incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron asignaciones exclusivas de las instancias de la función llamadas por la función principal en el árbol de llamadas.|  
  
## Valores de tiempo inclusivo transcurrido  
 Los valores de tiempo inclusivo transcurrido indican el tiempo que una función estuvo en la pila de llamadas.  Tiempo dedicado a funciones llamadas por la función y a llamadas al sistema operativo, tales como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión transcurrido**|Tiempo inclusivo transcurrido de todas las llamadas a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**% de tiempo inclusivo transcurrido**|Porcentaje de tiempo inclusivo transcurrido de la ejecución de la generación de perfiles que se empleó en el tiempo inclusivo transcurrido de esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Promedio de tiempo inclusivo transcurrido**|Tiempo inclusivo transcurrido medio de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo inclusivo máximo transcurrido**|Tiempo inclusivo transcurrido máximo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo inclusivo mínimo transcurrido**|Tiempo inclusivo transcurrido mínimo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
  
## Valores de tiempo exclusivo transcurrido  
 Los valores de tiempo exclusivo transcurrido indican el tiempo que una función se estuvo ejecutando directamente en la parte superior de la pila de llamadas.  El tiempo incluye el tiempo de las llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada\/salida.  Sin embargo, el tiempo no incluye el tiempo total invertido en las funciones llamadas por la función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión transcurrido**|Tiempo exclusivo transcurrido de todas las llamadas a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**% de tiempo exclusivo transcurrido**|Porcentaje de tiempo exclusivo transcurrido total de la ejecución de la generación de perfiles que se empleó en el tiempo exclusivo transcurrido de esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Promedio de tiempo exclusivo transcurrido**|Tiempo exclusivo transcurrido medio de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo exclusivo máximo transcurrido**|Tiempo exclusivo transcurrido máximo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo exclusivo mínimo transcurrido**|Tiempo exclusivo transcurrido mínimo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
  
## Valores de tiempo inclusivo de aplicación  
 Los valores de tiempo inclusivo de aplicación indican el tiempo que una función estuvo en la pila de llamadas.  El valor no incluye el tiempo dedicado a llamadas al sistema operativo, como en los cambios de contexto y en las operaciones de entrada\/salida.  El tiempo incluye el tiempo total invertido en las funciones secundarias llamadas por la función.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de inclusión de la aplicación**|Tiempo inclusivo de aplicación de todas las llamadas a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**% de tiempo de aplicación \(inclusive\)**|Porcentaje de tiempo inclusivo transcurrido de la ejecución de la generación de perfiles que se empleó en el tiempo inclusivo de aplicación de esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Promedio de tiempo inclusivo de aplicación**|Tiempo inclusivo de aplicación medio de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo inclusivo máximo de aplicación**|Tiempo inclusivo de aplicación máximo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo inclusivo mínimo de aplicación**|Tiempo inclusivo de aplicación mínimo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
  
## Valores de tiempo exclusivo de aplicación  
 Los valores exclusivos de la aplicación indican el tiempo invertido en la función, excepto el tiempo invertido en las funciones secundarias que fueron llamadas por la función.  El tiempo también excluye las llamadas al sistema operativo, como cambios de contexto y operaciones de entrada\/salida.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de exclusión de la aplicación**|Tiempo exclusivo de aplicación de todas las llamadas a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**% de tiempo de aplicación \(exclusive\)**|Porcentaje de tiempo exclusivo transcurrido de la ejecución de la generación de perfiles que se empleó en el tiempo exclusivo de aplicación de esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Promedio de tiempo exclusivo de aplicación**|Tiempo exclusivo de aplicación medio de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo exclusivo máximo de aplicación**|Tiempo exclusivo de aplicación máximo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|  
|**Tiempo exclusivo mínimo de aplicación**|Tiempo exclusivo de aplicación mínimo de una llamada a esta función cuando fue llamada por la función principal en el árbol de llamadas.|