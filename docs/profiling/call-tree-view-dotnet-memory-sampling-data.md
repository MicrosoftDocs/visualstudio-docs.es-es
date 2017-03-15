---
title: "Vista &#193;rbol de llamadas: Datos de muestreo de memoria .NET del generador de perfiles | Microsoft Docs"
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
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista &#193;rbol de llamadas: Datos de muestreo de memoria .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Árbol de llamadas muestra las rutas de ejecución de funciones que se atravesaron en la aplicación para la que se generan perfiles.  La raíz del árbol es el punto de entrada a la aplicación o el componente.  Cada nodo de función muestra todas las funciones a las que llamó y los datos de asignación de memoria de .NET sobre dichas llamadas a función.  
  
 Los valores de la vista Árbol de llamadas son para las instancias de la función a las que llamó la función principal en el árbol de llamadas.  Los valores de porcentaje se calculan comparando el valor de instancia de función con el número total o el tamaño de las asignaciones en la ejecución de asignación de perfiles.  
  
## Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas se puede expandir y puede resaltar la ruta de acceso de ejecución del proceso o la función que creó el mayor objeto de memoria o el mayor número de objetos de memoria.  Para mostrar la ruta de acceso más activa, haga clic con el botón secundario del mouse en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## Establecer el nodo raíz del árbol de llamadas  
 Cada uno de los procesos de la generación de perfiles se muestra como nodo raíz.  Para establecer el nodo de inicio de la vista Árbol de llamadas en un nodo diferente, haga clic con el botón secundario del mouse en el nodo que desee establecer como nodo de inicio y, a continuación, seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado.  Puede restablecer el nodo raíz en el nodo que estaba viendo; haga clic con el botón secundario del mouse en la ventana Vista Árbol de llamadas y seleccione **Restablecer raíz**.  
  
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
|**Nivel**|Profundidad de la función en el árbol de llamadas.|  
|**Asignaciones de inclusión**|El número de objetos asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron objeto de asignaciones inclusivas por parte de esta función.|  
|**Asignaciones de exclusión**|El número de objetos asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número no incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron asignaciones exclusivas de las instancias de la función llamadas por la función principal en el árbol de llamadas.|  
|**Bytes inclusivos**|El número de bytes en memoria asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones inclusivas de esta función.|  
|**Bytes exclusivos**|El número de bytes en memoria asignados por las instancias de esta función a los que llamó la función principal en el árbol de llamadas.  Este número no incluye asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que fueron asignaciones exclusivas de esta función.|  
  
## Vea también  
 [Vista Árbol de llamadas \- Instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)