---
title: "C&#243;mo: Utilizar la ventana Subprocesos de GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
  - "vs.debug.gputhreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, subprocesos de GPU (ventana)"
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar la ventana Subprocesos de GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Desde la ventana Subprocesos de GPU, puede examinar y trabajar con los subprocesos que se ejecutan en la GPU de la aplicación que esté depurando.  Para obtener más información sobre las aplicaciones que se ejecutan en la GPU, vea [Información general sobre C\+\+ AMP](/visual-cpp/parallel/amp/cpp-amp-overview).  
  
 La ventana Subprocesos de GPU contiene una tabla en la que cada fila representa un grupo de subprocesos de la GPU que tienen los mismos valores en todas las columnas.  Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas.  Puede marcar, quitar el marcador, inmovilizar \(suspender\) y retomar \(reanudar\) los subprocesos desde la ventana Subprocesos de GPU.  Las columnas siguientes se muestran en la ventana Subprocesos de GPU:  
  
-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
-   La columna del subproceso activo, en la que una flecha amarilla indica un subproceso activo.  Una flecha indica un subproceso en el que la ejecución interrumpió el depurador.  
  
-   La columna **Recuento de subprocesos**, que muestra el número de subprocesos en la misma ubicación.  
  
-   La columna **Línea**, que muestra la línea de código en la que se encuentra cada grupo de subprocesos.  
  
-   La columna **Dirección**, que muestra la dirección de instrucción en la que se encuentra cada grupo de subprocesos.  De forma predeterminada, se oculta esta columna.  
  
-   La columna **Ubicación**, que es la ubicación en el código fuente.  
  
-   La columna **Estado**, que muestra si el subproceso está activo, bloqueado, sin iniciar o completado.  
  
-   La columna **Mosaico**, que muestra el índice del mosaico para los subprocesos de la fila.  
  
 El encabezado de la tabla muestra el mosaico y el subproceso que aparecen.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para mostrar la ventana Subprocesos de GPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En la ventana **Páginas de propiedades** del proyecto, en **Propiedades de configuración**, elija **Depuración**.  
  
3.  En la lista **Depurador para iniciar**, seleccione **Depurador local de Windows**.  En la lista **Tipo de depurador**, seleccione **Solo GPU**.  Debe elegir este depurador para interrumpir en los puntos de interrupción del código que se ejecuta en la GPU.  
  
4.  Elija el botón **Aceptar**.  
  
5.  Establezca un punto de interrupción en el código de GPU.  
  
6.  En la barra de menús, elija **Depurar**, **Iniciar depuración**.  Espere hasta que la aplicación llegue al punto de interrupción.  
  
7.  En la barra de menús, elija **Depurar**, **Ventanas**, **Subprocesos de GPU**.  
  
### Para cambiar a un subproceso activo diferente  
  
-   Haga doble clic en la columna. \(Teclado: seleccione la fila y elija Entrar\).  
  
### Para mostrar un mosaico y un subproceso determinados  
  
1.  Elija el botón **Expandir selector de subprocesos** en la ventana Subprocesos de GPU.  
  
2.  Escriba los valores para el mosaico y el subproceso en los cuadros de texto.  
  
3.  Elija el botón que tiene una flecha.  
  
### Mostrar u ocultar columnas  
  
-   Abra el menú contextual de la ventana Subprocesos de GPU, elija **Columnas** y, a continuación, elija la columna que desea mostrar u ocultar.  
  
### Para ordenar por una columna  
  
-   Seleccione el encabezado de la columna.  
  
### Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana Subprocesos de GPU, elija **Agrupar por** y, a continuación, elija uno de los nombres de columna que aparecen.  Elija **Ninguno** para desagrupar los subprocesos.  
  
### Para inmovilizar o reanudar una fila de subprocesos  
  
-   Abra el menú contextual de la fila y elija **Inmovilizar** o **Reanudar**.  
  
### Para marcar o quitar el marcador de una fila de subprocesos  
  
-   Seleccione la columna de marcas del subproceso, o abra el menú contextual del subproceso y elija **Marcar** o **Quitar marcador**.  
  
### Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana Subprocesos de GPU.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Utilizar la Ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Tutorial: Depurar una aplicación de C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)