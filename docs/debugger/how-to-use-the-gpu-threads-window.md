---
title: Visualización de subprocesos de GPU en el depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbb49a1017fb0bc65300f3c16050db4954e1103
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348722"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Procedimiento Uso de la ventana Subprocesos de GPU (C++)
Desde la ventana Subprocesos de GPU, puede examinar y trabajar con los subprocesos que se ejecutan en la GPU de la aplicación que esté depurando. Para obtener más información sobre las aplicaciones que se ejecutan en la GPU, vea [Información general sobre C++ AMP](/cpp/parallel/amp/cpp-amp-overview).

 La ventana Subprocesos de GPU contiene una tabla en la que cada fila representa un grupo de subprocesos de la GPU que tienen los mismos valores en todas las columnas. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos desde la ventana Subprocesos de GPU. Las columnas siguientes se muestran en la ventana Subprocesos de GPU:

- La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.

- La columna de subproceso actual, donde una flecha amarilla indica el subproceso actual.

- Columna **Recuento de subprocesos**, que muestra el número de subprocesos en la misma ubicación.

- Columna **Línea**, que muestra la línea de código en la que se encuentra cada grupo de subprocesos.

- Columna **Dirección**, que muestra la dirección de instrucción en la que se encuentra cada grupo de subprocesos. De forma predeterminada, se oculta esta columna.

- Columna **Ubicación**, que es la ubicación en el código fuente.

- Columna **Estado**, que muestra si el subproceso está activo, bloqueado, sin iniciar o completado.

- Columna **Mosaico**, que muestra el índice del mosaico para los subprocesos de la fila.

  El encabezado de la tabla muestra el mosaico y el subproceso que aparecen.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>Para mostrar la ventana Subprocesos de GPU

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

2. En la ventana **Páginas de propiedades** del proyecto, en **Propiedades de configuración**, elija **Depuración**.

3. En la lista **Depurador para iniciar**, seleccione **Depurador local de Windows**. En la lista **Tipo de depurador**, seleccione **Solo GPU**. Debe elegir este depurador para interrumpir en los puntos de interrupción del código que se ejecuta en la GPU.

4. Elija el botón **Aceptar** .

5. Establezca un punto de interrupción en el código de GPU.

6. En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.

7. En la barra de menús, elija **Depurar**, **Ventanas**, **Subprocesos de GPU**.

### <a name="to-switch-to-a-different-thread"></a>Para cambiar a un subproceso diferente

- Haga doble clic en la columna. (Teclado: seleccione la fila y elija Entrar).

### <a name="to-display-a-particular-tile-and-thread"></a>Para mostrar un mosaico y un subproceso determinados

1. Elija el botón **Expandir selector de subprocesos** en la ventana Subprocesos de GPU.

2. Escriba los valores para el mosaico y el subproceso en los cuadros de texto.

3. Elija el botón que tiene una flecha.

### <a name="to-display-or-hide-a-column"></a>Mostrar u ocultar columnas

- Abra el menú contextual de la ventana Subprocesos de GPU, elija **Columnas** y después elija la columna que desea mostrar u ocultar.

### <a name="to-sort-by-a-column"></a>Para ordenar por una columna

- Seleccione el encabezado de la columna.

### <a name="to-group-threads"></a>Para agrupar subprocesos

- Abra el menú contextual de la ventana Subprocesos de GPU, elija **Agrupar por** y después elija uno de los nombres de columna que aparecen. Elija **Ninguno** para desagrupar los subprocesos.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>Para inmovilizar o reanudar una fila de subprocesos

- Abra el menú contextual de la fila y elija **Inmovilizar** o **Reanudar**.

### <a name="to-flag-or-unflag-a-row-of-threads"></a>Para marcar o quitar el marcador de una fila de subprocesos

- Seleccione la columna de marcas del subproceso, o abra el menú contextual del subproceso y elija **Marcar** o **Quitar marcador**.

### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados

- Elija el botón de marcador en la ventana Subprocesos de GPU.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)
- [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)