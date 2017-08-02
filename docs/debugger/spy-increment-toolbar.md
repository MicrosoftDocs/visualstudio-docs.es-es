---
title: "Spy++ Toolbar | Microsoft Docs"
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
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La barra de herramientas aparece bajo la barra de menús en Spy\+\+.  Para mostrar u ocultar la barra de herramientas, en el menú **Ver**, haga clic en **Barra de herramientas**.  
  
 Los controles siguientes están disponibles en la barra de herramientas.  
  
## Lista de UIElement  
  
|Button|Efecto|  
|------------|------------|  
|![Botón Ventanas de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_windows.gif "Icon\_Spy\+\+\_Windows")|Muestra una vista de árbol de las ventanas y controles del sistema.  Para obtener más información, vea [Windows View](../debugger/windows-view.md).|  
|![Botón Procesos de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_processes.gif "Icon\_Spy\+\+\_Processes")|Muestra una vista de árbol de los procesos del sistema.  Para obtener más información, vea [Processes View](../debugger/processes-view.md).|  
|![Botón Subprocesos de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_threads.gif "Icon\_Spy\+\+\_Threads")|Muestra una vista de árbol de los subprocesos del sistema.  Para obtener más información, vea [Threads View](../debugger/threads-view.md).|  
|![Botón Mensajes de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_messages.gif "Icon\_Spy\+\+\_Messages")|Crea una ventana para mostrar los mensajes de ventana y abre el cuadro de diálogo **Opciones de mensajes** para poder seleccionar la ventana cuyos mensajes se mostrarán y seleccionar también otras opciones.  Para obtener más información, vea [Messages View](../debugger/messages-view.md).|  
|![Botón Iniciar registro de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_startlog.gif "Icon\_Spy\+\+\_StartLog")|Inicia el registro de mensajes y muestra la secuencia de mensajes.  Este control sólo está disponible cuando una ventana **Mensajes** es la ventana activa.  Para obtener más información, vea [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botón Detener registro de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_stoplog.gif "Icon\_Spy\+\+\_StopLog")|Detiene el registro de mensajes y la presentación de la secuencia de mensajes.  Este control sólo está disponible cuando una ventana **Mensajes** es la ventana activa.  Para obtener más información, vea [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botón Opciones de registro de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_logoptions.gif "Icon\_Spy\+\+\_LogOptions")|Muestra el cuadro de diálogo [Opciones de mensaje](../debugger/message-options-dialog-box.md).  Use este cuadro de diálogo para seleccionar las ventanas y tipos de mensaje que desea ver.  Este control sólo está disponible cuando una ventana **Mensajes** es la ventana activa.|  
|![Botón para borrar registro de Spy&#43;&#43;](~/docs/debugger/media/spy--_clearlog.gif "Spy\+\+\_ClearLog")|Borra el contenido de la ventana **Mensajes** activa.  Este control sólo está disponible cuando una ventana **Mensajes** es la ventana activa.|  
|![Botón Buscar ventana de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_findwindow.gif "Icon\_Spy\+\+\_FindWindow")|Abre el cuadro de diálogo [Buscar ventana](../debugger/find-window-dialog-box.md), que permite establecer los criterios de búsqueda de ventanas, las propiedades de presentación o los mensajes.  Para obtener más información, vea [How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|  
|![Botón para buscar primera ventana de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_window.gif "Icon\_Spy\+\+\_Window")|Busca una ventana, proceso, subproceso o mensaje coincidente en la vista actual.|  
|![Botón Buscar siguiente ventana de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_nextwindow.gif "Icon\_Spy\+\+\_NextWindow")|Busca la siguiente ventana, proceso, subproceso o mensaje coincidente en la vista actual.  Este control \(y el comando de menú relacionado\) solo está disponible cuando hay un resultado de búsqueda válido que no es único.  Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, generará resultados únicos, ya que solo hay una ventana en el árbol de la ventana con ese identificador; en esta instancia, **Buscar siguiente** no está disponible.|  
|![Botón Buscar ventana anterior de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_prevwindow.gif "Icon\_Spy\+\+\_PrevWindow")|Busca la ventana, proceso, subproceso o mensaje anterior coincidente en la vista actual.  Este control \(y el comando de menú relacionado\) solo está disponible cuando hay un resultado de búsqueda válido que no es único.  Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, generará resultados únicos, ya que solo hay una ventana en el árbol de la ventana con ese identificador; en esta instancia, **Buscar anterior** no está disponible.|  
|![Botón Explorador de propiedades de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_propexp.gif "Icon\_Spy\+\+\_PropExp")|Muestra las propiedades de la ventana seleccionada en la vista Ventanas.|  
|![Botón Actualizar de Spy&#43;&#43;](~/docs/debugger/media/icon_spy--_refresh.gif "Icon\_Spy\+\+\_Refresh")|Actualiza las vistas del sistema.|  
  
## Vea también  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)