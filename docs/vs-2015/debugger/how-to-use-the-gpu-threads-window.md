---
title: Filtrar Utilice la ventana de subprocesos GPU | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee086109faa43976c9c8172cbc3af677ac140b5e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998762"
---
# <a name="how-to-use-the-gpu-threads-window"></a>Filtrar Uso de la ventana Subprocesos de GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Desde la ventana Subprocesos de GPU, puede examinar y trabajar con los subprocesos que se ejecutan en la GPU de la aplicación que esté depurando. Para obtener más información acerca de las aplicaciones que se ejecutan en la GPU, vea [Introducción a C++ AMP](http://msdn.microsoft.com/library/9e593b06-6e3c-43e9-8bae-6d89efdd39fc).  
  
 La ventana Subprocesos de GPU contiene una tabla en la que cada fila representa un grupo de subprocesos de la GPU que tienen los mismos valores en todas las columnas. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos desde la ventana Subprocesos de GPU. Las columnas siguientes se muestran en la ventana Subprocesos de GPU:  
  
- La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
- La columna del subproceso activo, en la que una flecha amarilla indica un subproceso activo. Una flecha indica un subproceso en el que la ejecución interrumpió el depurador.  
  
- Columna **Recuento de subprocesos**, que muestra el número de subprocesos en la misma ubicación.  
  
- Columna **Línea**, que muestra la línea de código en la que se encuentra cada grupo de subprocesos.  
  
- Columna **Dirección**, que muestra la dirección de instrucción en la que se encuentra cada grupo de subprocesos. De forma predeterminada, se oculta esta columna.  
  
- Columna **Ubicación**, que es la ubicación en el código fuente.  
  
- Columna **Estado**, que muestra si el subproceso está activo, bloqueado, sin iniciar o completado.  
  
- Columna **Mosaico**, que muestra el índice del mosaico para los subprocesos de la fila.  
  
  El encabezado de la tabla muestra el mosaico y el subproceso que aparecen.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>Para mostrar la ventana Subprocesos de GPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En la ventana **Páginas de propiedades** del proyecto, en **Propiedades de configuración**, elija **Depuración**.  
  
3.  En la lista **Depurador para iniciar**, seleccione **Depurador local de Windows**. En la lista **Tipo de depurador**, seleccione **Solo GPU**. Debe elegir este depurador para interrumpir en los puntos de interrupción del código que se ejecuta en la GPU.  
  
4.  Elija el botón **Aceptar** .  
  
5.  Establezca un punto de interrupción en el código de GPU.  
  
6.  En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
7.  En la barra de menús, elija **Depurar**, **Ventanas**, **Subprocesos de GPU**.  
  
### <a name="to-change-to-a-different-active-thread"></a>Para cambiar a un subproceso activo diferente  
  
-   Haga doble clic en la columna. (Teclado: Seleccione la fila y elija ENTRAR).  
  
### <a name="to-display-a-particular-tile-and-thread"></a>Para mostrar un mosaico y un subproceso determinados  
  
1.  Elija el botón **Expandir selector de subprocesos** en la ventana Subprocesos de GPU.  
  
2.  Escriba los valores para el mosaico y el subproceso en los cuadros de texto.  
  
3.  Elija el botón que tiene una flecha.  
  
### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas  
  
-   Abra el menú contextual de la ventana Subprocesos de GPU, elija **Columnas** y después elija la columna que desea mostrar u ocultar.  
  
### <a name="to-sort-by-a-column"></a>Para ordenar por una columna  
  
-   Seleccione el encabezado de la columna.  
  
### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana Subprocesos de GPU, elija **Agrupar por** y después elija uno de los nombres de columna que aparecen. Elija **Ninguno** para desagrupar los subprocesos.  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Para inmovilizar o reanudar una fila de subprocesos  
  
-   Abra el menú contextual de la fila y elija **Inmovilizar** o **Reanudar**.  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>Para marcar o quitar el marcador de una fila de subprocesos  
  
-   Seleccione la columna de marcas del subproceso, o abra el menú contextual del subproceso y elija **Marcar** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana Subprocesos de GPU.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
