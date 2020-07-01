---
title: Establecimiento de una inspección de variables en subprocesos paralelos | Microsoft Docs
ms.date: 04/25/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb0d5ac60ea5ab89b02a624488b5df4f8a7164b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348631"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Establecimiento de una inspección de variables en subprocesos paralelos de Visual Studio (C#, Visual Basic y C++)
En la ventana Inspección paralela, puede mostrar simultáneamente los valores que contiene una expresión en varios subprocesos. Cada fila representa un subproceso que se ejecuta en una aplicación, pero un subproceso puede representarse en varias filas. Para ser más exactos, cada fila representa una llamada de función cuya signatura de función coincide con la función en el marco de pila actual. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos. Las siguientes columnas se muestran en la ventana **Inspección paralela**:

- La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.

- La columna de subproceso actual, donde una flecha amarilla indica el subproceso actual (una flecha verde con una cola rizada indica que un subproceso no actual tiene el contexto del depurador actual).

- Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.

  > [!TIP]
  > Para mostrar información sobre la tarea en la ventana **Inspección paralela**, primero debe abrir la ventana **Tarea**.

- Columnas en blanco *Agregar inspección*, en las que puede escribir las expresiones que quiera examinar.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Para mostrar la ventana Inspección paralela

1. Establezca un punto de interrupción en el código.

2. En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.

3. En la barra de menús, elija **Depurar**, **Ventanas**, **Inspección paralela** y después elija una ventana de inspección. Puede abrir hasta cuatro ventanas.

### <a name="to-add-a-watch-expression"></a>Para agregar una expresión de inspección

- Seleccione una de las columnas en blanco *Agregar inspección* y, a continuación, escriba una expresión de inspección.

### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso

- Seleccione la columna de marcas de la fila (primera columna) o abra el menú contextual del subproceso y, a continuación, elija **Marcar** o **Quitar marcador**.

### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados

- Elija el botón **Mostrar solo marcados** en la esquina superior izquierda de la ventana **Inspección paralela**.

### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso

- Haga doble clic en la columna del subproceso actual (segunda columna). (Teclado: seleccione la fila y presione Entrar).

### <a name="to-sort-a-column"></a>Para ordenar una columna

- Seleccione el encabezado de la columna.

### <a name="to-group-threads"></a>Para agrupar subprocesos

- Abra el menú contextual de la ventana Inspección paralela, elija **Agrupar por** y después seleccione el elemento del submenú adecuado.

### <a name="to-freeze-or-thaw-threads"></a>Para inmovilizar o reanudar los subprocesos

- Abra el menú contextual de la fila y elija **Inmovilizar** o **Reanudar**.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Para exportar los datos de la ventana Inspección paralela

- Elija el botón **Abrir en Excel** y después seleccione **Abrir en Excel** o **Exportar a CSV**.

### <a name="to-filter-by-a-boolean-expression"></a>Para filtrar por una expresión booleana

- Escriba una expresión booleana en el cuadro **Filtrar por expresión booleana**. El depurador evalúa la expresión para cada contexto del subproceso. Solo se muestran las filas con el valor `true`.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: usar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)
- [Tutorial: Depurar una aplicación de C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)