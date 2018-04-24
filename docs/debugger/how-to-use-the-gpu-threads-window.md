---
title: Ver los subprocesos de GPU en el depurador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c99e0e1bf64a6a88778d4bfcf27a796916a0f044
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-the-gpu-threads-window"></a>Cómo: Utilizar la ventana Subprocesos de GPU
Desde la ventana Subprocesos de GPU, puede examinar y trabajar con los subprocesos que se ejecutan en la GPU de la aplicación que esté depurando. Para obtener más información acerca de las aplicaciones que se ejecutan en la GPU, consulte [Introducción a C++ AMP](/cpp/parallel/amp/cpp-amp-overview).  
  
 La ventana Subprocesos de GPU contiene una tabla en la que cada fila representa un grupo de subprocesos de la GPU que tienen los mismos valores en todas las columnas. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos desde la ventana Subprocesos de GPU. Las columnas siguientes se muestran en la ventana Subprocesos de GPU:  
  
-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
-   La columna del subproceso actual, en el que una flecha amarilla indica el subproceso actual.  
  
-   El **el número de subprocesos** columna, que muestra el número de subprocesos en la misma ubicación.  
  
-   El **línea** columna, que muestra la línea de código donde se encuentra cada grupo de subprocesos.  
  
-   El **dirección** columna, que muestra la dirección de instrucción que se encuentra cada grupo de subprocesos. De forma predeterminada, se oculta esta columna.  
  
-   El **ubicación** columna, que es la ubicación en el código fuente.  
  
-   El **estado** columna, que muestra si el subproceso está activo, bloqueado, no se ha iniciado o completa.  
  
-   El **icono** columna, que muestra el índice del mosaico para los subprocesos de la fila.  
  
 El encabezado de la tabla muestra el mosaico y el subproceso que aparecen.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Para mostrar la ventana Subprocesos de GPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** ventana para el proyecto, en **propiedades de configuración**, elija **depuración**.  
  
3.  En el **depurador para iniciar** lista, seleccione **depurador Local de Windows**. En el **tipo de depurador** lista, seleccione **solo GPU**. Debe elegir este depurador para interrumpir en los puntos de interrupción del código que se ejecuta en la GPU.  
  
4.  Elija el botón **Aceptar** .  
  
5.  Establezca un punto de interrupción en el código de GPU.  
  
6.  En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
7.  Una barra de menús, elija **depurar**, **Windows**, **subprocesos de GPU**.  
  
### <a name="to-switch-to-a-different-thread"></a>Para cambiar a un subproceso diferente  
  
-   Haga doble clic en la columna. (Teclado: seleccione la fila y elija Entrar).  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Para mostrar un mosaico y un subproceso determinados  
  
1.  Elija la **expandir selector de subprocesos** botón en la ventana subprocesos de GPU.  
  
2.  Escriba los valores para el mosaico y el subproceso en los cuadros de texto.  
  
3.  Elija el botón que tiene una flecha.  
  
### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas  
  
-   Abra el menú contextual de la ventana subprocesos de GPU, elija **columnas**y, a continuación, elija la columna que desea mostrar u ocultar.  
  
### <a name="to-sort-by-a-column"></a>Para ordenar por una columna  
  
-   Seleccione el encabezado de la columna.  
  
### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana subprocesos de GPU, elija **Group By**y, a continuación, elija uno de los nombres de columna que se muestran. Elija **ninguno** para desagrupar los subprocesos.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Para inmovilizar o reanudar una fila de subprocesos  
  
-   Abra el menú contextual para la fila y elija **inmovilizar** o **reanudar**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Para marcar o quitar el marcador de una fila de subprocesos  
  
-   Seleccione la columna de marca para el subproceso, o abra el menú contextual para el subproceso y elija **marca** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana Subprocesos de GPU.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: utilizar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)