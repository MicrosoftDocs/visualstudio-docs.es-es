---
title: Barra de herramientas de Spy++ | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154014"
---
# <a name="spy-toolbar"></a>Barra de herramientas de Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barra de herramientas aparece en la barra de menús de Spy++. Para mostrar u ocultar la barra de herramientas, en el menú **Vista**, haga clic en **Barra de herramientas**.  
  
 Estos son los controles que están disponibles en la barra de herramientas.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
|Botón|Efecto|  
|------------|------------|  
|![Botón Ventanas de Spy&#43;&#43;](../debugger/media/icon-spy-windows.gif "Icon_Spy++_Windows")|Muestra una vista de árbol de las ventanas y los controles del sistema. Para más información, vea [Vista Ventanas](../debugger/windows-view.md).|  
|![Botón Procesos de Spy&#43;&#43;](../debugger/media/icon-spy-processes.gif "Icon_Spy++_Processes")|Muestra una vista de árbol de los procesos del sistema. Para más información, vea [Vista Procesos](../debugger/processes-view.md).|  
|![Botón Subprocesos de Spy&#43;&#43;](../debugger/media/icon-spy-threads.gif "Icon_Spy++_Threads")|Muestra una vista de árbol de los subprocesos del sistema. Para más información, vea [Vista Subprocesos](../debugger/threads-view.md).|  
|![Botón Mensajes de Spy&#43;&#43;](../debugger/media/icon-spy-messages.gif "Icon_Spy++_Messages")|Crea una ventana para mostrar los mensajes de ventana y abre el cuadro de diálogo **Opciones de mensaje** para que pueda seleccionar la ventana cuyos mensajes se van a mostrar y seleccionar también otras opciones. Para más información, vea [Vista Mensajes](../debugger/messages-view.md).|  
|![Botón Iniciar registro de Spy&#43;&#43;](../debugger/media/icon-spy-startlog.gif "Icon_Spy++_StartLog")|Inicia el registro de mensajes y muestra el flujo de mensajes. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa. Para obtener más información, vea [Cómo: Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botón Detener registro de Spy&#43;&#43;](../debugger/media/icon-spy-stoplog.gif "Icon_Spy++_StopLog")|Detiene el registro de mensajes y la presentación de la secuencia de mensajes. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa. Para obtener más información, vea [Cómo: Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Botón Opciones de registro de Spy&#43;&#43;](../debugger/media/icon-spy-logoptions.gif "Icon_Spy++_LogOptions")|Muestra el cuadro de diálogo [Opciones de mensaje](../debugger/message-options-dialog-box.md). En este cuadro de diálogo puede seleccionar los tipos de mensaje y de ventanas que se van a ver. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa.|  
|![Botón Borrar registro de Spy&#43;&#43;](../debugger/media/spy-clearlog.gif "Spy++_ClearLog")|Borra el contenido de la ventana **Mensajes** activa. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa.|  
|![Botón Buscar ventana de Spy&#43;&#43;](../debugger/media/icon-spy-findwindow.gif "Icon_Spy++_FindWindow")|Abre el cuadro de diálogo [Buscar ventana](../debugger/find-window-dialog-box.md), que permite establecer los criterios de búsqueda de la ventana y mostrar las propiedades o los mensajes. Para obtener más información, vea [Cómo: Uso de la herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md).|  
|![Botón Buscar primero de Spy&#43;&#43;](../debugger/media/icon-spy-window.gif "Icon_Spy++_Window")|Busca en la vista actual una ventana, proceso, subproceso o mensaje que coincida.|  
|![Botón Buscar siguiente de Spy&#43;&#43;](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy++_NextWindow")|Busca en la vista actual la siguiente ventana, proceso, subproceso o mensaje que coincida. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar siguiente** no está disponible.|  
|![Botón Buscar anterior de Spy&#43;&#43;](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy++_PrevWindow")|Busca en la vista actual la ventana, el proceso, el subproceso o el mensaje anterior que coincida. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar anterior** no está disponible.|  
|![Botón Explorador de propiedades de Spy&#43;&#43;](../debugger/media/icon-spy-propexp.gif "Icon_Spy++_PropExp")|Muestra las propiedades de la ventana seleccionada en la vista Ventanas.|  
|![Botón Actualizar de Spy&#43;&#43;](../debugger/media/icon-spy-refresh.gif "Icon_Spy++_Refresh")|Actualiza las vistas del sistema.|  
  
## <a name="see-also"></a>Consulte también  
 [Usar Spy + +](../debugger/using-spy-increment.md)   
 [Vistas de Spy + +](../debugger/spy-increment-views.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)
