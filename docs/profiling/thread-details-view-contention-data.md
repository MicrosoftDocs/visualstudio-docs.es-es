---
title: "Vista Detalles del subproceso: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
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
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "Detalles del subproceso (vista)"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Detalles del subproceso: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Detalles del subproceso presenta un gráfico de escala de tiempo de los eventos de bloqueo en el subproceso seleccionado de una ejecución de generación de perfiles originados por las contenciones sobre recursos.  Un evento de bloqueo se produce cuando el subproceso se ve obligado a suspender la ejecución porque otro subproceso ha bloqueado el acceso a un recurso.  
  
 Esta vista representa la escala de tiempo de ejecución del subproceso como una barra horizontal y los eventos de bloqueo como barras verticales en una escala de tiempo horizontal para el subproceso.  Si es necesario, puede acercar una sección de la escala de tiempo para ver los eventos individuales.  Para ver la ruta de acceso de ejecución de las funciones que dieron lugar al evento, haga clic en la barra del evento.  Las funciones aparecen en la ventana Pila de llamadas.  Si está disponible el código fuente de una función, puede hacer clic en el nombre de la función para editar el archivo de origen en el IDE de Visual Studio.  
  
## Navegar en la escala de tiempo  
  
#### Para acercar un segmento de la escala de tiempo  
  
-   Haga clic y arrastre el puntero del mouse para seleccionar un área de la escala de tiempo.  
  
     Al soltar el mouse, la vista amplía el segmento de tiempo seleccionado.  Puede repetir el proceso para ampliar con mayor detalle.  El cuadro de desplazamiento de la barra de desplazamiento temporal representa el tamaño relativo del segmento de tiempo que se muestra en la vista.  
  
#### Para alejar una escala de tiempo  
  
-   Haga clic en **Alejar** para volver al nivel de zoom anterior.  
  
-   Haga clic en **Restablecer zoom** para mostrar la escala de tiempo completa en la vista.  
  
#### Para ver la pila de llamadas de un evento  
  
-   En el gráfico de escala de tiempo, haga clic en la barra vertical que representa el evento.  
  
#### Para ver o editar el código fuente de una función en la pila de llamadas  
  
-   En la ventana Pila de llamadas, haga clic en el nombre de la función.  
  
 El código fuente de la función debe formar parte del proyecto actual.  
  
#### Para ver los eventos de contención de un recurso en todos los subprocesos de la ejecución de generación de perfiles  
  
-   En el gráfico de escala de tiempo, haga clic en el nombre o identificador del recurso.  
  
     Aparece la [Detalles de recursos \(Vista\)](../profiling/resource-details-view-contention-data.md) del recurso seleccionado.  
  
#### Para ver los datos de contención del subproceso en la ventana Procesos  
  
-   En el gráfico de escala de tiempo, haga clic en **Total**.  
  
     Aparece [Vista Proceso](../profiling/process-view-contention-data.md) con el subproceso seleccionado.