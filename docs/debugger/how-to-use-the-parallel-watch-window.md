---
title: "Establece una inspección en las Variables de subprocesos paralelos | Documentos de Microsoft"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 570f77cddede91a81dc15200ebcf02b27f1a4f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Establece una inspección en las Variables de subprocesos en paralelo en Visual Studio
En la ventana Inspección paralela, puede mostrar simultáneamente los valores que contiene una expresión en varios subprocesos. Cada fila representa un subproceso que se ejecuta en una aplicación, pero un subproceso puede representarse en varias filas. Para ser más exactos, cada fila representa una llamada de función cuya signatura de función coincide con la función en el marco de pila actual. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos. Las columnas siguientes se muestran en la **inspección paralela** ventana:  
  
-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
-   La columna del subproceso actual, en el que una flecha amarilla indica el subproceso actual (la flecha verde con una cola rizada indica que un subproceso actual no tiene el contexto actual del depurador).  
  
-   Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.  
  
    > [!TIP]
    >  En información de tarea dislay en el **inspección paralela** ventana, primero debe abrir la **tarea** ventana.  
  
-   El espacio en blanco *Agregar inspección* columnas, donde puede escribir expresiones que desee examinar.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Para mostrar la ventana Inspección paralela  
  
1.  Establezca un punto de interrupción en el código.  
  
2.  En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
3.  En la barra de menús, elija **depurar**, **Windows**, **inspección paralela**y, a continuación, elija una ventana Inspección. Puede abrir hasta cuatro ventanas.  
  
### <a name="to-add-a-watch-expression"></a>Para agregar una expresión de inspección  
  
-   Seleccione uno de la prueba en blanco *Agregar inspección* columnas y, a continuación, escriba una expresión de inspección.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso  
  
-   Seleccione la columna de marca de la fila (primera columna), o abra el menú contextual para el subproceso y elija **marca** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija la **mostrar marcadas únicamente** situado en la esquina superior izquierda de la **inspección paralela** ventana.  
  
### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso  
  
-   Haga doble clic en la columna del subproceso actual (segunda columna). (Teclado: seleccione la fila y presione Entrar).  
  
### <a name="to-sort-a-column"></a>Para ordenar una columna  
  
-   Seleccione el encabezado de la columna.  
  
### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana Inspección paralela, elija **Group By**y, a continuación, elija el elemento del submenú adecuado.  
  
### <a name="to-freeze-or-thaw-threads"></a>Para inmovilizar o reanudar los subprocesos  
  
-   Abra el menú contextual para la fila y elija **inmovilizar** o **reanudar**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Para exportar los datos de la ventana Inspección paralela  
  
-   Elija la **abierto en Excel** botón y, a continuación, elija **abierto en Excel** o **exportar a CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Para filtrar por una expresión booleana  
  
-   Escriba una expresión booleana en el **filtrar por expresión booleana** cuadro. El depurador evalúa la expresión para cada contexto del subproceso. Solo se muestran las filas con el valor `true`.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: utilizar la ventana de subprocesos GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)