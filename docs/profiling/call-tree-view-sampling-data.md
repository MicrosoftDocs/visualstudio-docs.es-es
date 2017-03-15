---
title: "Vista &#193;rbol de llamadas: datos de muestreo del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles mediante muestreo, vista Árbol de llamadas"
  - "Vista Árbol de llamadas"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Vista &#193;rbol de llamadas: datos de muestreo del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Árbol de llamadas muestra las rutas de ejecución de funciones que se atravesaron en la aplicación para la que se generan perfiles.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 La raíz del árbol es el punto de entrada a la aplicación o el componente.  Cada nodo de función enumera todas las funciones a las que llamó y los datos de rendimiento sobre dichas llamadas a función.  
  
 Los valores de la vista Árbol de llamadas son para las instancias de la función a las que llamó la función principal en el árbol de llamadas.  Los valores de porcentaje se calculan comparando el valor de instancia de función con el número total de muestras de la ejecución de asignación de perfiles.  
  
## Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas se puede expandir y puede resaltar la ruta de acceso de ejecución del proceso o la función que se muestreó con más frecuencia.  Para mostrar la ruta de acceso más activa, haga clic con el botón secundario del mouse en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## Establecer el nodo raíz del árbol de llamadas  
 Cada uno de los procesos de la generación de perfiles se muestra como nodo raíz.  Para establecer el nodo de inicio de la vista Árbol de llamadas, haga clic con el botón secundario del mouse en el nodo que desea establecer como nodo de inicio y, a continuación, seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado.  Para restablecer el nodo raíz en el nodo original, haga clic con el botón secundario del mouse en la ventana de la vista Árbol de llamadas y, a continuación, seleccione **Restablecer raíz**.  
  
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
|**Nivel**|Profundidad de esta función en el árbol de llamadas.  Solo en informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Ejemplos de exclusión**|Número de muestras recopiladas en esta función cuando fue llamada por la función primaria en el árbol de llamadas.  Este número no incluye las muestras recopiladas en funciones a las que llamó la función.|  
|**Porcentaje de muestras exclusivas**|Porcentaje de muestras exclusivas de esta función cuando fue llamada por la función primaria del árbol de llamadas con respecto a todas las muestras de la ejecución de generación de perfiles.|  
|**Ejemplos de inclusión**|Número de muestras recopiladas en esta función cuando fue llamada por la función primaria en el árbol de llamadas.  Este número incluye las muestras recopiladas en funciones a las que llamó la función.|  
|**Porcentaje de muestras inclusivas**|Porcentaje de muestras inclusivas de esta función cuando fue llamada por la función primaria del árbol de llamadas con respecto a todas las muestras de la ejecución de generación de perfiles.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas \- Muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Vista Árbol de llamadas \- Instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)