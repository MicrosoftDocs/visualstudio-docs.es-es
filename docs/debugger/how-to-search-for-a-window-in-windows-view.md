---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede buscar una ventana concreta en la vista Ventanas mediante su identificador, leyenda o clase, así como mediante una combinación de su leyenda y clase, como criterios de búsqueda.  También puede especificar la dirección inicial de la búsqueda.  Los campos del cuadro de diálogo mostrarán los atributos de la ventana seleccionada en el árbol de ventanas.  
  
 Empiece con el árbol expandido en el segundo nivel \(todas las ventanas que son elementos secundarios del escritorio\) para que pueda identificar las ventanas del nivel del escritorio por su nombre de clase y título.  Cuando haya elegido una ventana en el nivel del escritorio, puede expandir ese nivel para buscar una ventana secundaria concreta.  
  
### Para buscar una ventana en la vista Ventanas  
  
1.  Organice las ventanas de modo que estén visibles Spy\+\+, la ventana [Vista Ventanas](../debugger/windows-view.md) y la ventana de destino.  
  
2.  En el menú **Buscar**, elija **Buscar ventana**.  
  
     Se abrirá el [cuadro de diálogo Buscar ventana](../debugger/window-search-dialog-box.md).  
  
    > [!TIP]
    >  Para reducir el desorden de la pantalla, seleccione la opción **Ocultar Spy\+\+**.  Esta opción oculta la ventana principal de Spy\+\+ y deja únicamente el cuadro de diálogo **Buscar ventana** visible encima de las demás aplicaciones.  La ventana principal de Spy\+\+ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy\+\+**.  
  
3.  Arrastre la **herramienta de búsqueda** sobre la ventana de destino.  Mientras se arrastra la herramienta, el cuadro de diálogo **Buscar ventana** muestra los detalles de la ventana seleccionada.  
  
     \-O bien\-  
  
     Si conoce el identificador de la ventana que desea \(por ejemplo, a través del depurador\), puede escribirlo en el cuadro **Identificador**.  
  
     \-O bien\-  
  
     Si conoce la leyenda o la clase de la ventana que desea, puede escribirlos en los cuadros de texto **Leyenda** y **Clase**, y borrar el cuadro de texto **Identificador**.  
  
4.  Elija **Arriba** o **Abajo** como dirección inicial de la búsqueda.  
  
5.  Haga clic en **Aceptar**.  
  
     Si se encuentra una ventana coincidente, se resalta en la ventana [Vista Ventanas](../debugger/windows-view.md).