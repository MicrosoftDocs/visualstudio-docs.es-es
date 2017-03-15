---
title: "Vista &#193;rbol de llamadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "Árbol de llamadas (vista)"
  - "informes de rendimiento, Árbol de llamadas (vista)"
  - "informes de herramientas de generación de perfiles, Árbol de llamadas (vista)"
  - "herramientas de generación de perfiles, Árbol de llamadas (vista)"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Vista &#193;rbol de llamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Árbol de llamadas muestra las rutas de ejecución de funciones que se atravesaron en la aplicación para la que se generan perfiles.  La raíz del árbol es el punto de entrada a la aplicación o el componente.  Cada nodo de función enumera todas las funciones a las que llamó y los datos de rendimiento sobre dichas llamadas a función.  
  
 La vista Árbol de llamadas también puede expandir y resaltar la ruta de ejecución de una función que haya requerido más tiempo o que se haya sometido a muestreo con mayor frecuencia.  Para mostrar la ruta de acceso con mayor incidencia en el rendimiento, haga clic con el botón secundario en la función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
 Cada uno de los procesos de la generación de perfiles se muestra como nodo raíz.  Para establecer el nodo de inicio de la vista Árbol de llamadas, haga clic con el botón secundario del mouse en el nodo que desee establecer como nodo de inicio y, a continuación, seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado.  Puede restablecer el nodo que estaba viendo como nodo raíz.  En la ventana de la vista Árbol de llamadas, haga clic con el botón secundario del mouse y, a continuación, seleccione **Restablecer raíz**.  
  
 La vista Árbol de llamadas se puede personalizar para agregar o quitar columnas.  Haga clic con el botón secundario del mouse en la **barra de título Nombre de columna** y, a continuación, seleccione **Agregar o quitar columnas**.  
  
 La vista Árbol de llamadas se puede configurar para la reducción de ruido limitando la cantidad de datos presentados.  Al utilizar la reducción de ruido, los problemas de rendimiento destacan más en la vista.  Cuando los problemas de rendimiento se distinguen con facilidad, el análisis es más sencillo.  Para obtener más información, vea [Cómo: Configurar la reducción de ruido en las vistas de informes](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Si la reducción de ruido está configurada de modo que se muestre una advertencia cuando está habilitada, se mostrará una barra de información en el informe.  
  
 Para obtener más información sobre las definiciones de las columnas de la vista Árbol de llamadas, vea lo siguiente:  
  
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)  
  
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Vista Árbol de llamadas \- Muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Vista Árbol de llamadas](../profiling/call-tree-view-contention-data.md)  
  
## Vea también  
 [Vistas de informes de las herramientas de generación de perfiles](../profiling/performance-report-views.md)   
 [Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)