---
title: "C&#243;mo: Utilizar puntos de interrupci&#243;n con XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Utilizar puntos de interrupci&#243;n con XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede establecer los puntos de interrupción en una hoja de estilos XSLT o en el documento de origen XML.Si establece un punto de interrupción en una etiqueta, cuando comienza la ejecución el punto de interrupción se traslada a la siguiente instrucción que tiene información de línea de código fuente.  
  
 Para obtener más información, vea [Debugging Basics: Breakpoints](http://msdn.microsoft.com/es-es/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## Establecer un punto de interrupción en una hoja de estilos  
 Se pueden establecer los puntos de interrupción en las etiquetas de apertura y de cierre, y en los nodos de texto de una hoja de estilos XSLT.También pueden establecerse en el código de un bloque de scripts.  
  
#### Para establecer un punto de interrupción en una hoja de estilos  
  
1.  Abra una hoja de estilos en el Editor XML.  
  
2.  Coloque el cursor en la ubicación del punto de interrupción, haga clic con el botón secundario, seleccione **Punto de interrupción** y haga clic en **Insertar punto de interrupción**.  
  
3.  Haga clic en el botón Examinar \(**...**\) en el campo **Entrada** de la ventana Propiedades del documento.  
  
4.  Busque el documento de origen XML y haga clic en **Abrir**.  
  
     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.  
  
5.  Haga clic en el botón **Depurar XSL** en la barra de herramientas del Editor XML.  
  
## Establecer un punto de interrupción en un documento de origen XML  
 Pueden establecer los puntos de interrupción en los elementos, atributos, nodos de espacio de nombres, comentarios, instrucción de procesamiento y nodos de texto de un documento de origen XML.No puede establecerse un punto de interrupción en el nodo de documentos ni en un nodo de espacio de nombres heredado del elemento primario.  
  
#### Para establecer un punto de interrupción en un documento de origen XML  
  
1.  Abra el documento XML en el Editor XML.  
  
2.  Coloque el cursor en la ubicación del punto de interrupción, haga clic con el botón secundario, seleccione **Punto de interrupción** y haga clic en **Insertar punto de interrupción**.  
  
3.  Haga clic en el botón Examinar \(**...**\) en el campo **Hoja de estilos** de la ventana Propiedades del documento.  
  
4.  Busque el documento de origen XML y haga clic en **Abrir**.  
  
     De esta forma se establece el archivo del documento de origen que se utilizará para la transformación XSLT.  
  
5.  Haga clic en el botón **Depurar XSL** en la barra de herramientas del Editor XML.  
  
## Vea también  
 [Tutorial: Depurar una hoja de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)