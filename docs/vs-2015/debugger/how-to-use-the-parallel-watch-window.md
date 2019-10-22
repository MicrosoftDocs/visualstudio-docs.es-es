---
title: Procedimiento Utilice la ventana Inspección paralela | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697493"
---
# <a name="how-to-use-the-parallel-watch-window"></a>Procedimiento Utilice la ventana Inspección paralela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la ventana Inspección paralela, puede mostrar simultáneamente los valores que contiene una expresión en varios subprocesos. Cada fila representa un subproceso que se ejecuta en una aplicación, pero un subproceso puede representarse en varias filas. Para ser más exactos, cada fila representa una llamada de función cuya signatura de función coincide con la función en el marco de pila actual. Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas. Puede marcar, quitar el marcador, inmovilizar (suspender) y retomar (reanudar) los subprocesos. Las siguientes columnas se muestran en la ventana **Inspección paralela**:  
  
- La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
- La columna de marcos, en la que una flecha indica el marco seleccionado.  
  
- Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.  
  
  > [!TIP]
  > Debe abrir el **tareas en paralelo** ventana para mostrar la información de la tarea en el **inspección paralela** ventana.  
  
- El  **\<Agregar inspección >** columna, donde puede escribir expresiones para inspeccionar.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>Para mostrar la ventana Inspección paralela  
  
1. Establezca un punto de interrupción en el código.  
  
2. En la barra de menús, seleccione **Depurar**, **Iniciar depuración**. Espere hasta que la aplicación llegue al punto de interrupción.  
  
3. En la barra de menús, elija **Depurar**, **Ventanas**, **Inspección paralela** y después elija una ventana de inspección. Puede abrir hasta cuatro ventanas.  
  
### <a name="to-add-a-watch-expression"></a>Para agregar una expresión de inspección  
  
- Seleccione  **\<Agregar inspección >** y, a continuación, especifique una expresión de inspección.  
  
### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso  
  
- Seleccione la columna de marca para la fila, o abra el menú contextual para el subproceso y elija **marca** o **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
- Elija el botón Mostrar solo marcados en la esquina superior izquierda de la **inspección paralela** ventana.  
  
### <a name="to-switch-frames"></a>Para cambiar los marcos  
  
- Haga doble clic en la columna del marco. (Teclado: Seleccione la fila y presione ENTRAR).  
  
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
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Uso de la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
