---
title: "C&#243;mo: Utilizar la Ventana Inspecci&#243;n paralela | Microsoft Docs"
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
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, inspección paralela (ventana)"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar la Ventana Inspecci&#243;n paralela
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En la ventana Inspección paralela, puede mostrar simultáneamente los valores que contiene una expresión en varios subprocesos.  Cada fila representa un subproceso que se ejecuta en una aplicación, pero un subproceso puede representarse en varias filas.  Para ser más exactos, cada fila representa una llamada de función cuya signatura de función coincide con la función en el marco de pila actual.  Puede ordenar, reordenar, quitar y agrupar los elementos incluidos en las columnas.  Puede marcar, quitar el marcador, inmovilizar \(suspender\) y retomar \(reanudar\) los subprocesos.  Las siguientes columnas se muestran en la ventana **Inspección paralela**:  
  
-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.  
  
-   La columna de marcos, en la que una flecha indica el marco seleccionado.  
  
-   Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.  
  
    > [!TIP]
    >  Debe abrir la ventana **Tareas paralelas** para mostrar información sobre la tarea en la ventana **Inspección paralela**.  
  
-   La columna **\<Agregar inspección\>**, en la que puede escribir las expresiones que desee examinar.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para mostrar la ventana Inspección paralela  
  
1.  Establezca un punto de interrupción en el código.  
  
2.  En la barra de menús, elija **Depurar**, **Iniciar depuración**.  Espere hasta que la aplicación llegue al punto de interrupción.  
  
3.  En la barra de menús, elija **Depurar**, **Ventanas**, **Inspección paralela** y, a continuación, elija una ventana de inspección.  Puede abrir hasta cuatro ventanas.  
  
### Para agregar una expresión de inspección  
  
-   Seleccione **\<Agregar inspección\>** y, a continuación, especifique una expresión de inspección.  
  
### Para marcar o quitar marcador de un subproceso  
  
-   Seleccione la columna de marcas de la fila, o abra el menú contextual del subproceso y, a continuación, elija **Marcar** o **Quitar marcador**.  
  
### Para mostrar solo los subprocesos marcados  
  
-   Elija el botón Mostrar solo marcados en la esquina superior izquierda de la ventana **Inspección paralela**.  
  
### Para cambiar los marcos  
  
-   Haga doble clic en la columna del marco. \(Teclado: seleccione la fila y presione Entrar\).  
  
### Para ordenar una columna  
  
-   Seleccione el encabezado de la columna.  
  
### Para agrupar subprocesos  
  
-   Abra el menú contextual de la ventana Inspección paralela, elija **Agrupar por** y, a continuación, seleccione el elemento del submenú adecuado.  
  
### Para inmovilizar o reanudar los subprocesos  
  
-   Abra el menú contextual de la fila y elija **Inmovilizar** o **Reanudar**.  
  
### Para exportar los datos de la ventana Inspección paralela  
  
-   Elija el botón **Abrir en Excel** y, a continuación, seleccione **Abrir en Excel** o **Exportar a CSV**.  
  
### Para filtrar por una expresión booleana  
  
-   Escriba una expresión booleana en el cuadro **Filtrar por expresión booleana**.  El depurador evalúa la expresión para cada contexto del subproceso.  Solo se muestran las filas con el valor `true`.  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Utilizar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Tutorial: Depurar una aplicación de C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)