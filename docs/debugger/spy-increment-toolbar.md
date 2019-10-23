---
title: Barra de herramientas de Spy + + | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fa1dfe0917fece3c814678295c5abd6013b426b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729740"
---
# <a name="spy-toolbar"></a>Barra de herramientas de Spy++
La barra de herramientas aparece en la barra de menús de Spy + +. Para mostrar u ocultar la barra de herramientas, en el menú **Ver** , haga clic en **barra de herramientas**.

 Los controles siguientes están disponibles en la barra de herramientas.

## <a name="uielement-list"></a>Lista de UIElement

|Botón|Efecto|
|------------|------------|
|![Botón&#43; &#43; Spy Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Muestra una vista de árbol de las ventanas y los controles del sistema. Para obtener más información, vea [vista ventanas](../debugger/windows-view.md).|
|![Botón&#43; &#43; de procesos de Spy](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Muestra una vista de árbol de los procesos del sistema. Para obtener más información, consulte la [vista procesos](../debugger/processes-view.md).|
|![Botón&#43; &#43; de Spy threads](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Muestra una vista de árbol de los subprocesos del sistema. Para obtener más información, consulte [vista de subprocesos](../debugger/threads-view.md).|
|![Botón&#43; &#43; de mensajes de Spy](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Crea una ventana para mostrar los mensajes de la ventana y abre el cuadro de diálogo **Opciones de mensaje** para que pueda seleccionar la ventana cuyos mensajes se van a mostrar y seleccionar también otras opciones. Para obtener más información, consulte [vista mensajes](../debugger/messages-view.md).|
|![Botón&#43; &#43; de registro de inicio de Spy](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Inicia el registro de mensajes y muestra el flujo de mensajes. Este control solo está disponible cuando una ventana de **mensajes** es la ventana activa. Para obtener más información, consulte [Cómo: iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botón&#43; &#43; de detención del registro de Spy](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Detiene el registro de mensajes y la presentación de la secuencia de mensajes. Este control solo está disponible cuando una ventana de **mensajes** es la ventana activa. Para obtener más información, consulte [Cómo: iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botón&#43; &#43; opciones de registro de Spy](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Muestra el cuadro de diálogo [Opciones de mensaje](../debugger/message-options-dialog-box.md) . Utilice este cuadro de diálogo para seleccionar los tipos de mensajes y ventanas que se van a ver. Este control solo está disponible cuando una ventana de **mensajes** es la ventana activa.|
|![Botón&#43; &#43; desactivar registro de Spy](../debugger/media/spy--_clearlog.gif "_ClearLog de Spy + +")|Borra el contenido de la ventana **mensajes** activos. Este control solo está disponible cuando una ventana de **mensajes** es la ventana activa.|
|![Botón&#43; &#43; buscar ventana de Spy](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Abre el cuadro de diálogo [Buscar ventana](../debugger/find-window-dialog-box.md) , que permite establecer los criterios de búsqueda de la ventana y mostrar las propiedades o los mensajes. Para obtener más información, consulte [Cómo: usar la herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md).|
|![Botón&#43; &#43; buscar primera ventana de Spy](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Busca en la vista actual una ventana, un proceso, un subproceso o un mensaje coincidentes.|
|![Botón&#43; &#43; Buscar siguiente ventana de Spy](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Busca en la vista actual la siguiente ventana, proceso, subproceso o mensaje coincidente. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar siguiente** no está disponible.|
|![Botón&#43; &#43; buscar ventana anterior de Spy](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Busca en la vista actual la ventana coincidente anterior, el proceso, el subproceso o el mensaje. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar anterior** no está disponible.|
|![Botón&#43; &#43; explorador de propiedades de Spy](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Muestra las propiedades de la ventana seleccionada en la vista ventanas.|
|![Botón&#43; &#43; de actualización de Spy](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Actualiza las vistas del sistema.|

## <a name="see-also"></a>Vea también
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)