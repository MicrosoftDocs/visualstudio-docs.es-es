---
title: "How to: Use the Finder Tool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Window Finder Tool"
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Use the Finder Tool
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar la herramienta de búsqueda del cuadro de diálogo **Buscar ventana** para mostrar las propiedades o mensajes de una ventana.  La herramienta de búsqueda también puede encontrar ventanas secundarias deshabilitadas y distinguir qué ventana debe resaltar si las ventanas secundarias deshabilitadas están superpuestas.  
  
 ![Cuadro de diálogo Buscar ventana de Spy&#43;&#43;](../debugger/media/icon_spy--_find.png "Icon\_Spy\+\+\_Find")  
Herramienta de búsqueda del cuadro de diálogo Buscar ventana  
  
 En la ilustración anterior se muestra el cuadro de diálogo Buscar ventana después del paso 3 siguiente.  
  
### Para mostrar propiedades o mensajes de una ventana  
  
1.  Organice las ventanas de modo que estén visibles Spy\+\+ y la ventana de destino.  
  
2.  En el menú **Spy**, elija **Buscar ventana**.  
  
     Se abrirá el [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md).  
  
3.  Arrastre la **herramienta de búsqueda** sobre la ventana de destino.  
  
     Mientras se arrastra la herramienta, el cuadro de diálogo **Buscar ventana** muestra los detalles de la ventana seleccionada.  
  
     \-O bien\-  
  
     Si tiene el identificador de la ventana que desea examinar \(por ejemplo, lo copió del depurador\), escríbalo en el cuadro de texto **Identificador**.  
  
    > [!TIP]
    >  Para reducir el desorden de la pantalla, seleccione la opción **Ocultar Spy\+\+**.  Esta opción oculta la ventana principal de Spy\+\+ y deja únicamente el cuadro de diálogo **Buscar ventana** visible encima de las demás aplicaciones.  La ventana principal de Spy\+\+ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy\+\+**.  
  
4.  Bajo **Mostrar**, seleccione **Propiedades** o **Mensajes**.  
  
5.  Presione **Aceptar**.  
  
     Si seleccionó **Propiedades**, se abrirá el [cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md).  Si seleccionó **Mensajes**, se abrirá una ventana de [vista Mensajes](../debugger/messages-view.md).  
  
## Vea también  
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)