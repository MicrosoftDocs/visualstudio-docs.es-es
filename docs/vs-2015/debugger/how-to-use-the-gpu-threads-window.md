---
title: 'Cómo: utilizar la ventana de subprocesos GPU | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bf63fb2eedc03b62af46f3ecdf746aaee6dde09
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848675"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Cómo: Utilizar la ventana Subprocesos de GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Desde la ventana Subprocesos de GPU, puede examinar y trabajar con los subprocesos que se ejecutan en la GPU de la aplicación que esté depurando. Para obtener más información acerca de las aplicaciones que se ejecutan en la GPU, vea [Introducción a C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 La ventana Subprocesos de GPU contiene una tabla en la que cada fila representa un grupo de subprocesos de la GPU que tienen los mismos valores en todas las columnas. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos desde la ventana Subprocesos de GPU. Las columnas siguientes se muestran en la ventana Subprocesos de GPU:  
  
- La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
- La columna del subproceso activo, en la que una flecha amarilla indica un subproceso activo. Una flecha indica un subproceso en el que la ejecución interrumpió el depurador.  
  
- El **el número de subprocesos** columna, que muestra el número de subprocesos en la misma ubicación.  
  
- El **línea** columna, que muestra la línea de código donde se encuentra cada grupo de subprocesos.  
  
- El **dirección** columna, que muestra la dirección de la instrucción donde se encuentra cada grupo de subprocesos. De forma predeterminada, se oculta esta columna.  
  
- El **ubicación** columna, que es la ubicación en el código fuente.  
  
- El **estado** columna, que muestra si el subproceso está activo, bloqueado, no se ha iniciado o completa.  
  
- El **icono** columna, que muestra el índice de los subprocesos del mosaico de la fila.  
  
  El encabezado de la tabla muestra el mosaico y el subproceso que aparecen.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Para mostrar la ventana Subprocesos de GPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el **páginas de propiedades** ventana para el proyecto, bajo **propiedades de configuración**, elija **depuración**.  
  
3.  En el **depurador para iniciar** lista, seleccione **depurador Local de Windows**. En el **tipo de depurador** lista, seleccione **solo GPU**. Debe elegir este depurador para interrumpir en los puntos de interrupción del código que se ejecuta en la GPU.  
  
4.  Elija el botón **Aceptar** .  
  
5.  Establezca un punto de interrupción en el código de GPU.  
  
6.  En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
7.  Una barra de menús, elija **depurar**, **Windows**, **subprocesos de GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Para cambiar a un subproceso activo diferente  
  
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
  
-   Abra el menú contextual de la fila y elija **inmovilizar** o **reanudar**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Para marcar o quitar el marcador de una fila de subprocesos  
  
-   Seleccione la columna de marca para el subproceso, o abra el menú contextual para el subproceso y elija **marca** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana Subprocesos de GPU.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: utilizar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)



