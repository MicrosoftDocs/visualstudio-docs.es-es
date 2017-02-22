---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
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
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para buscar un subproceso concreto en la vista Subprocesos puede usar el identificador de subproceso o la cadena de módulo como criterio de búsqueda.  También puede especificar la dirección inicial de la búsqueda.  Los campos del cuadro de diálogo mostrarán los atributos del subproceso seleccionado en el árbol de subprocesos.  
  
### Para buscar un subproceso en la vista de subprocesos  
  
1.  Organice las ventanas de modo que estén visibles la ventana de Spy\+\+ y una ventana de [vista de subprocesos](../debugger/threads-view.md) activa.  
  
2.  En el menú **Buscar**, elija **Buscar subproceso**.  
  
     Se abrirá el [cuadro de diálogo Buscar subproceso](../debugger/thread-search-dialog-box.md).  
  
3.  Escriba el identificador de subproceso o una cadena de módulo como criterio de búsqueda.  
  
4.  Borre cualquier campo para el que no desee especificar valores.  
  
    > [!TIP]
    >  Para buscar todos los subprocesos que pertenecen a un módulo, borre el cuadro de texto **Subproceso** y escriba el nombre del módulo en el cuadro **Módulo**.  Después, use **Buscar siguiente** para seguir buscando subprocesos.  
  
5.  Elija **Arriba** o **Abajo** como dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un subproceso coincidente, se resalta en la ventana de la vista Subprocesos.