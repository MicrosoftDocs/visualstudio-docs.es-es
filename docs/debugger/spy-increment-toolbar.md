---
title: Barra de herramientas de Spy++ | Microsoft Docs
description: Conozca los elementos de la interfaz de usuario de la barra de herramientas de Spy++, que aparece en la barra de menús. Para mostrar u ocultar la barra de herramientas, en el menú Vista, haga clic en Barra de herramientas.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9dc2564a69c291055d53e358c084e7dd9c4d0506
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148200"
---
# <a name="spy-toolbar"></a>Barra de herramientas de Spy++
La barra de herramientas aparece en la barra de menús de Spy++. Para mostrar u ocultar la barra de herramientas, en el menú **Vista**, haga clic en **Barra de herramientas**.

 Estos son los controles que están disponibles en la barra de herramientas.

## <a name="uielement-list"></a>Lista de UIElement

|Botón|Efecto|
|------------|------------|
|![Botón Ventanas de Spy&#43;&#43;](../debugger/media/icon_spy--_windows.gif "Icon_Spy++_Windows")|Muestra una vista de árbol de las ventanas y los controles del sistema. Para más información, vea [Vista Ventanas](../debugger/windows-view.md).|
|![Botón Procesos de Spy&#43;&#43;](../debugger/media/icon_spy--_processes.gif "Icon_Spy++_Processes")|Muestra una vista de árbol de los procesos del sistema. Para más información, vea [Vista Procesos](../debugger/processes-view.md).|
|![Botón Subprocesos de Spy&#43;&#43;](../debugger/media/icon_spy--_threads.gif "Icon_Spy++_Threads")|Muestra una vista de árbol de los subprocesos del sistema. Para más información, vea [Vista Subprocesos](../debugger/threads-view.md).|
|![Botón Mensajes de Spy&#43;&#43;](../debugger/media/icon_spy--_messages.gif "Icon_Spy++_Messages")|Crea una ventana para mostrar los mensajes de ventana y abre el cuadro de diálogo **Opciones de mensaje** para que pueda seleccionar la ventana cuyos mensajes se van a mostrar y seleccionar también otras opciones. Para más información, vea [Vista Mensajes](../debugger/messages-view.md).|
|![Botón Iniciar registro de Spy&#43;&#43;](../debugger/media/icon_spy--_startlog.gif "Icon_Spy++_StartLog")|Inicia el registro de mensajes y muestra el flujo de mensajes. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa. Para obtener más información, vea [Cómo: Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botón Detener registro de Spy&#43;&#43;](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy++_StopLog")|Detiene el registro de mensajes y la presentación de la secuencia de mensajes. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa. Para obtener más información, vea [Cómo: Procedimiento Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Botón Opciones de registro de Spy&#43;&#43;](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy++_LogOptions")|Muestra el cuadro de diálogo [Opciones de mensaje](../debugger/message-options-dialog-box.md). En este cuadro de diálogo puede seleccionar los tipos de mensaje y de ventanas que se van a ver. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa.|
|![Botón Borrar registro de Spy&#43;&#43;](../debugger/media/spy--_clearlog.gif "Spy++_ClearLog")|Borra el contenido de la ventana **Mensajes** activa. Este control solo está disponible cuando una ventana **Mensajes** es la ventana activa.|
|![Botón Buscar ventana de Spy&#43;&#43;](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy++_FindWindow")|Abre el cuadro de diálogo [Buscar ventana](../debugger/find-window-dialog-box.md), que permite establecer los criterios de búsqueda de la ventana y mostrar las propiedades o los mensajes. Para obtener más información, vea [Cómo: Uso de la herramienta de búsqueda](../debugger/how-to-use-the-finder-tool.md).|
|![Botón Buscar primero de Spy&#43;&#43;](../debugger/media/icon_spy--_window.gif "Icon_Spy++_Window")|Busca en la vista actual una ventana, proceso, subproceso o mensaje que coincida.|
|![Botón Buscar siguiente de Spy&#43;&#43;](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy++_NextWindow")|Busca en la vista actual la siguiente ventana, proceso, subproceso o mensaje que coincida. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar siguiente** no está disponible.|
|![Botón Buscar anterior de Spy&#43;&#43;](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy++_PrevWindow")|Busca en la vista actual la ventana, el proceso, el subproceso o el mensaje anterior que coincida. Este control (y el comando de menú relacionado) solo está disponible cuando hay un resultado de búsqueda válido que no es único. Por ejemplo, cuando se usa un identificador de ventana como criterio de búsqueda en el árbol de ventanas, se generan resultados únicos porque solo hay una ventana en el árbol de ventanas que tiene ese identificador; en esta instancia, **Buscar anterior** no está disponible.|
|![Botón Explorador de propiedades de Spy&#43;&#43;](../debugger/media/icon_spy--_propexp.gif "Icon_Spy++_PropExp")|Muestra las propiedades de la ventana seleccionada en la vista Ventanas.|
|![Botón Actualizar de Spy&#43;&#43;](../debugger/media/icon_spy--_refresh.gif "Icon_Spy++_Refresh")|Actualiza las vistas del sistema.|

## <a name="see-also"></a>Vea también
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)