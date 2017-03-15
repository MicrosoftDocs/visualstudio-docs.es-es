---
title: "Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.processesview"
helpviewer_keywords: 
  - "Processes view"
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Procesos muestra un árbol de todos los procesos activos en el sistema.  Se incluyen el identificador de proceso y el nombre de módulo.  Use la vista Procesos si desea examinar un proceso del sistema, que normalmente se corresponde con un programa en ejecución.  Los procesos se identifican mediante nombres de módulo, o se designan como "procesos del sistema".  
  
 Microsoft Windows admite varios procesos.  Cada proceso puede tener uno o más subprocesos, y cada subproceso puede tener asociadas una o más ventanas de nivel superior.  Cada ventana de nivel superior puede poseer una serie de ventanas.  El símbolo \+ indica que hay un nivel contraído.  La vista contraída está formada por una línea por proceso.  Haga clic en el símbolo \+ para expandir el nivel.  
  
 Use la vista Procesos si desea examinar un proceso del sistema, que normalmente se corresponde con un programa en ejecución.  Los procesos se identifican mediante nombres de módulo, o se designan como "procesos del sistema". Para encontrar un proceso, contraiga el árbol y busque en la lista.  
  
## Procedimientos  
  
#### Para abrir la vista Procesos  
  
1.  En el menú **Spy**, elija **Procesos**.  
  
 ![Vista de procesos de Spy&#43;&#43;](../debugger/media/spy--_processes.png "Spy\+\+\_Processes")  
Vista Procesos de Spy\+\+  
  
 En la ilustración anterior se muestra la vista Procesos con los nodos de procesos y subprocesos expandidos.  
  
### En esta sección  
 [Buscar un proceso en la vista Procesos](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Explica cómo encontrar un proceso concreto en la vista Procesos.  
  
 [Mostrar las propiedades de los procesos](../debugger/how-to-display-process-properties.md)  
 Explica cómo mostrar más información sobre un mensaje.  
  
### Secciones relacionadas  
 [Vistas de Spy\+\+](../debugger/spy-increment-views.md)  
 Explica las vistas de árbol de Spy\+\+ de ventanas, mensajes, procesos y subprocesos.  
  
 [Usar Spy\+\+](../debugger/using-spy-increment.md)  
 Presenta la herramienta Spy\+\+ y explica cómo se puede usar.  
  
 [Cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md)  
 Se usa para buscar el nodo de un proceso concreto en la vista Procesos.  
  
 [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md)  
 Muestra las propiedades de un proceso seleccionado en la vista Procesos.  
  
 [Referencia de Spy\+\+](../debugger/spy-increment-reference.md)  
 Incluye secciones que describen los menús y cuadros de diálogo de Spy\+\+.