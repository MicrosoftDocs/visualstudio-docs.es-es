---
title: Barra de herramientas de Spy ++ | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a96a5765c98bf8e7d1c600fbd47478a88fa7175d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154014"
---
# <a name="spy-toolbar"></a>Barra de herramientas de Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barra de herramientas aparece debajo de la barra de menú de Spy ++. Para mostrar u ocultar la barra de herramientas en el **vista** menú, haga clic en **barra de herramientas**.  
  
 Los controles siguientes están disponibles en la barra de herramientas.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
|Botón|Efecto|  
|------------|------------|  
|![Spy&#43; &#43; Windows botón](../debugger/media/icon-spy-windows.gif "Icon_Spy ++ _Windows")|Muestra una vista de árbol de las ventanas y controles del sistema. Para obtener más información, consulte [Windows Vista](../debugger/windows-view.md).|  
|![Spy&#43; &#43; procesa botón](../debugger/media/icon-spy-processes.gif "Icon_Spy ++ _Processes")|Muestra una vista de árbol de los procesos del sistema. Para obtener más información, consulte [vista procesos](../debugger/processes-view.md).|  
|![Spy&#43; &#43; subprocesos botón](../debugger/media/icon-spy-threads.gif "Icon_Spy ++ _Threads")|Muestra una vista de árbol de los subprocesos del sistema. Para obtener más información, consulte [vista de subprocesos](../debugger/threads-view.md).|  
|![Spy&#43; &#43; mensajes botón](../debugger/media/icon-spy-messages.gif "Icon_Spy ++ _Messages")|Crea una ventana para mostrar los mensajes de ventana y abre el **opciones de mensaje** cuadro de diálogo para que pueda seleccionar la ventana cuyos mensajes se mostrarán y también seleccionar otras opciones. Para obtener más información, consulte [vista mensajes](../debugger/messages-view.md).|  
|![Spy&#43; &#43; botón Iniciar registro](../debugger/media/icon-spy-startlog.gif "Icon_Spy ++ _StartLog")|Inicia el registro de mensajes y muestra la secuencia de mensajes. Este control solo está disponible cuando una **mensajes** ventana es la ventana activa. Para obtener más información, consulte [Cómo Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; botón Detener registro](../debugger/media/icon-spy-stoplog.gif "Icon_Spy ++ _StopLog")|Registro y la visualización del flujo de mensajes, mensajes se detiene. Este control solo está disponible cuando una **mensajes** ventana es la ventana activa. Para obtener más información, vea [Cómo: Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; botón Opciones de registro](../debugger/media/icon-spy-logoptions.gif "Icon_Spy ++ _LogOptions")|Muestra el [opciones de mensaje](../debugger/message-options-dialog-box.md) cuadro de diálogo. Utilice este cuadro de diálogo para seleccionar windows y tipos de visualización de mensajes. Este control solo está disponible cuando una **mensajes** ventana es la ventana activa.|  
|![Spy&#43; &#43; registro botón Borrar](../debugger/media/spy-clearlog.gif "Spy ++ _ClearLog")|Borra el contenido de activo **mensajes** ventana. Este control solo está disponible cuando una **mensajes** ventana es la ventana activa.|  
|![Spy&#43; &#43; buscar botón ventana](../debugger/media/icon-spy-findwindow.gif "Icon_Spy ++ _FindWindow")|Se abre el [Buscar ventana](../debugger/find-window-dialog-box.md) cuadro de diálogo que le permite establecer los criterios de búsqueda de ventana y mostrar propiedades o mensajes. Para obtener más información, vea [Cómo: Uso de la herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; buscar el primer botón de ventana](../debugger/media/icon-spy-window.gif "Icon_Spy ++ _Window")|Busca la vista actual una ventana coincidente, proceso, subproceso o mensaje.|  
|![Spy&#43; &#43; botón Buscar siguiente ventana](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy ++ _NextWindow")|Busca la vista actual para la siguiente ventana coincidente, el proceso, subproceso o mensaje. Este control (y el comando de menú relacionados) están disponibles solo cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, produce resultados únicos porque hay sólo una ventana en el árbol de la ventana que tiene ese identificador; en este caso, **Buscar siguiente** no está disponible.|  
|![Spy&#43; &#43; buscar botón ventana anterior](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy ++ _PrevWindow")|Busca la vista actual de la ventana coincidente anterior, el proceso, subproceso o mensaje. Este control (y el comando de menú relacionados) están disponibles solo cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de la ventana, produce resultados únicos porque hay sólo una ventana en el árbol de la ventana que tiene ese identificador; en este caso, **Buscar anterior** no está disponible.|  
|![Spy&#43; &#43; botón Explorador de propiedades](../debugger/media/icon-spy-propexp.gif "Icon_Spy ++ _PropExp")|Muestra las propiedades de la ventana que está seleccionado en la vista de Windows.|  
|![Spy&#43; &#43; botón Actualizar](../debugger/media/icon-spy-refresh.gif "Icon_Spy ++ actualiza_r")|Actualiza las vistas del sistema.|  
  
## <a name="see-also"></a>Vea también  
 [Usar Spy++](../debugger/using-spy-increment.md)   
 [Vistas de Spy++](../debugger/spy-increment-views.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)
