---
title: Establece una inspección en Variables de subprocesos paralelos | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a142b512c5bbaf5d93dc0302aa39db92fb7c7ae
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808079"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio"></a>Establece una inspección en Variables en subprocesos en paralelo en Visual Studio
En la ventana Inspección paralela, puede mostrar simultáneamente los valores que contiene una expresión en varios subprocesos. Cada fila representa un subproceso que se ejecuta en una aplicación, pero un subproceso puede representarse en varias filas. Para ser más exactos, cada fila representa una llamada de función cuya signatura de función coincide con la función en el marco de pila actual. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos. Las columnas siguientes se muestran en el **inspección paralela** ventana:  
  
-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
-   La columna del subproceso actual, en el que una flecha amarilla indica que el subproceso actual (una flecha verde con una cola rizada indica que un subproceso distinto del actual tiene el contexto actual del depurador).  
  
-   Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.  
  
    > [!TIP]
    >  A la información de tareas para mostrar del **inspección paralela** ventana, primero debe abrir el **tarea** ventana.  
  
-   El espacio en blanco *Agregar inspección* columnas, donde puede escribir expresiones para inspeccionar.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Para mostrar la ventana Inspección paralela  
  
1.  Establezca un punto de interrupción en el código.  
  
2.  En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
3.  En la barra de menús, elija **depurar**, **Windows**, **inspección paralela**y, a continuación, elija una ventana Inspección. Puede abrir hasta cuatro ventanas.  
  
### <a name="to-add-a-watch-expression"></a>Para agregar una expresión de inspección  
  
-   Seleccione uno del blanco *Agregar inspección* columnas y, a continuación, escriba una expresión de inspección.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso  
  
-   Seleccione la columna de marca de la fila (primera columna), o abra el menú contextual para el subproceso y elija **marca** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija la **mostrar marcadas únicamente** situado en la esquina superior izquierda de la **inspección paralela** ventana.  
  
### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso  
  
-   Haga doble clic en la columna del subproceso actual (segunda columna). (Teclado: seleccione la fila y presione Entrar).  
  
### <a name="to-sort-a-column"></a>Para ordenar una columna  
  
-   Seleccione el encabezado de la columna.  
  
### <a name="to-group-threads"></a>Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana Inspección paralela, elija **Group By**y, a continuación, elija el elemento de submenú adecuado.  
  
### <a name="to-freeze-or-thaw-threads"></a>Para inmovilizar o reanudar los subprocesos  
  
-   Abra el menú contextual de la fila y elija **inmovilizar** o **reanudar**.  
  
### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Para exportar los datos de la ventana Inspección paralela  
  
-   Elija la **abrir en Excel** botón y, a continuación, elija **abrir en Excel** o **exportar a CSV**.  
  
### <a name="to-filter-by-a-boolean-expression"></a>Para filtrar por una expresión booleana  
  
-   Escriba una expresión booleana en el **filtrar por expresión booleana** cuadro. El depurador evalúa la expresión para cada contexto del subproceso. Solo se muestran las filas con el valor `true`.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: utilizar la ventana de subprocesos GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)