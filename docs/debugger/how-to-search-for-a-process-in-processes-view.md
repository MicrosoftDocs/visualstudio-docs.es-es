---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para buscar un proceso concreto en la vista Procesos, se puede usar su identificador de proceso o cadena de módulo como criterio de búsqueda.  También puede especificar la dirección inicial de la búsqueda.  Los campos del cuadro de diálogo mostrarán los atributos del proceso seleccionado en el árbol de procesos.  
  
### Para buscar un proceso en la vista Procesos  
  
1.  Organice las ventanas de modo que estén visibles la ventana de Spy\+\+ y una ventana de [vista Procesos](../debugger/processes-view.md) activa.  
  
2.  En el menú **Buscar**, elija **Buscar proceso**.  
  
     Se abrirá el [cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md).  
  
3.  Escriba el identificador de proceso o una cadena de módulo como criterio de búsqueda.  
  
4.  Borre cualquier campo para el que no desee especificar valores.  
  
    > [!TIP]
    >  Para buscar todos los procesos que pertenecen a un módulo, borre el cuadro **Proceso** y escriba el nombre del módulo en el cuadro **Módulo**.  Después, use **Buscar siguiente** para seguir buscando procesos.  
  
5.  Elija **Arriba** o **Abajo** como dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un proceso coincidente, se resalta en la ventana de la **vista Proceso**.