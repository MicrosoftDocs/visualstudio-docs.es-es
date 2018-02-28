---
title: Barra de herramientas de Spy ++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a9d9331e8767c4d815a6f62b7952414ced966d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="spy-toolbar"></a>Barra de herramientas de Spy++
La barra de herramientas aparece debajo de la barra de menús de Spy ++. Para mostrar u ocultar la barra de herramientas, en la **vista** menú, haga clic en **barra de herramientas**.  
  
 Los siguientes controles están disponibles en la barra de herramientas.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
|Botón|Efecto|  
|------------|------------|  
|![Spy &#43; &#43; Botón de Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy ++ _Windows")|Muestra una vista de árbol de las ventanas y controles en el sistema. Para obtener más información, consulte [Windows Vista](../debugger/windows-view.md).|  
|![Spy &#43; &#43; Procesa botón](../debugger/media/icon_spy--_processes.gif "Icon_Spy ++ _Processes")|Muestra una vista de árbol de los procesos del sistema. Para obtener más información, consulte [vista procesos](../debugger/processes-view.md).|  
|![Spy &#43; &#43; Botón de subprocesos](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Muestra una vista de árbol de los subprocesos del sistema. Para obtener más información, consulte [vista de subprocesos](../debugger/threads-view.md).|  
|![Spy &#43; &#43; Mensajes de botón](../debugger/media/icon_spy--_messages.gif "Icon_Spy ++ _Messages")|Crea una ventana para mostrar mensajes de ventana y abre la **opciones de mensaje** cuadro de diálogo para que pueda seleccionar la ventana cuyos mensajes se mostrarán y seleccionar otras opciones. Para obtener más información, consulte [vista mensajes](../debugger/messages-view.md).|  
|![Spy &#43; &#43; Botón Iniciar registro](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Inicia el registro de mensajes y muestra la secuencia de mensajes. Este control solo está disponible cuando un **mensajes** ventana es la ventana activa. Para obtener más información, consulte [Cómo: iniciar y detener la presentación del registro de mensaje](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy &#43; &#43; Botón Detener registro](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy ++ _StopLog")|Deja de mensaje de registro y la presentación de la secuencia de mensajes. Este control solo está disponible cuando un **mensajes** ventana es la ventana activa. Para obtener más información, consulte [Cómo: iniciar y detener la presentación del registro de mensaje](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy &#43; &#43; Botón Opciones de registro](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy ++ _LogOptions")|Muestra el [opciones de mensaje](../debugger/message-options-dialog-box.md) cuadro de diálogo. Utilice este cuadro de diálogo para seleccionar ventanas y tipos de visualización de mensaje. Este control solo está disponible cuando un **mensajes** ventana es la ventana activa.|  
|![Spy &#43; &#43; Borrar registro botón](../debugger/media/spy--_clearlog.gif "Spy ++ _ClearLog")|Borra el contenido de activos **mensajes** ventana. Este control solo está disponible cuando un **mensajes** ventana es la ventana activa.|  
|![Spy &#43; &#43; Botón de la ventana Buscar](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy ++ _FindWindow")|Se abre la [Buscar ventana](../debugger/find-window-dialog-box.md) cuadro de diálogo que le permite establecer los criterios de búsqueda de ventana y mostrar las propiedades o mensajes. Para obtener más información, consulte [Cómo: usar la herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy &#43; &#43; Buscar el primer botón de la ventana](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Busca la vista actual una ventana coincidente, el proceso, el subproceso o el mensaje.|  
|![Spy &#43; &#43; Botón Buscar siguiente ventana](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Busca en la vista actual de la siguiente ventana coincidente, el proceso, el subproceso o el mensaje. Este control (y el comando de menú relacionado) sólo están disponibles cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, produce resultados únicos porque hay sólo una ventana en el árbol de la ventana que tiene ese identificador; en este caso, **Buscar siguiente** no está disponible.|  
|![Spy &#43; &#43; Buscar anterior botón ventana](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Busca en la vista actual de la ventana coincidente anterior, el proceso, el subproceso o el mensaje. Este control (y el comando de menú relacionado) sólo están disponibles cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, produce resultados únicos porque hay sólo una ventana en el árbol de la ventana que tiene ese identificador; en este caso, **Buscar anterior** no está disponible.|  
|![Spy &#43; &#43; Botón Explorador de propiedades](../debugger/media/icon_spy--_propexp.gif "Icon_Spy ++ _PropExp")|Muestra las propiedades de la ventana que está seleccionado en la vista de Windows.|  
|![Spy &#43; &#43; Botón Actualizar](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Actualiza las vistas del sistema.|  
  
## <a name="see-also"></a>Vea también  
 [Usar Spy ++](../debugger/using-spy-increment.md)   
 [Vistas de Spy ++](../debugger/spy-increment-views.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)