---
title: Vista Mensajes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157478"
---
# <a name="messages-view"></a>Vista Mensajes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cada ventana tiene una secuencia de mensajes asociada. La ventana de vista Mensajes muestra esta secuencia de mensajes. Se muestran el identificador de ventana, el código del mensaje y el mensaje. También puede crear una vista Mensajes para un subproceso o un proceso. Esto permite ver los mensajes enviados a todas las ventanas que pertenecen a un proceso o un subproceso específico, lo que es especialmente útil para capturar los mensajes de inicialización de la ventana.  
  
 Aquí se muestra una ventana de vista Mensajes típica. Fíjese en que la primera columna contiene el identificador de ventana y la segunda contiene un código de mensaje (que se explica en [Códigos de mensaje](../debugger/message-codes.md)). Los parámetros de mensaje descodificados y los valores devueltos están a la derecha.  
  
 ![Vista de mensajes de&#43;&#43; de Spy](../debugger/media/spy-messagesview.png "_MessagesView de Spy + +")  
Vista de mensajes de Spy++  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Para abrir una vista Mensajes para una ventana, proceso o subproceso  
  
1. Mueva el foco a una [vista Ventanas](../debugger/windows-view.md), [vista Procesos](../debugger/processes-view.md) o [vista Subprocesos](../debugger/threads-view.md).  
  
2. Busque el nodo del elemento cuyos mensajes quiere examinar y selecciónelo.  
  
3. En el menú **Spy**, seleccione **Mensajes de registro**.  
  
     Se abre el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md).  
  
4. Seleccione las opciones del mensaje que quiere mostrar.  
  
5. Presione **Aceptar** para empezar a registrar mensajes.  
  
     Se abre la ventana de una vista Mensajes y se agrega un menú **Mensajes** a la barra de herramientas de Spy++. En función de las opciones seleccionadas, los mensajes comienzan a transmitirse a la ventana de la vista Mensajes activa.  
  
6. Cuando tenga suficientes mensajes, seleccione **Detener registro** en el menú **Mensajes**.  
  
## <a name="in-this-section"></a>En esta sección  
 [Controlar la vista de mensajes](../debugger/how-to-control-messages-view.md)  
 Explica cómo administrar la vista de mensajes.  
  
 [Buscar un mensaje en la vista mensajes](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Explica cómo buscar un mensaje específico en la vista mensajes.  
  
 [Iniciar y detener la presentación del registro de mensajes](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explica cómo iniciar y detener el registro de mensajes.  
  
 [Códigos de mensaje](../debugger/message-codes.md)  
 Define los códigos de los mensajes que aparecen en la vista mensajes.  
  
 [Mostrar Propiedades de mensaje](../debugger/how-to-display-message-properties.md)  
 Cómo mostrar más información acerca de un mensaje.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Vistas de Spy++](../debugger/spy-increment-views.md)  
 Explica las vistas de árbol de Spy + + de ventanas, mensajes, procesos y subprocesos.  
  
 [Usar Spy++](../debugger/using-spy-increment.md)  
 Presenta la herramienta Spy + + y explica cómo se puede usar.  
  
 [Cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md)  
 Se usa para seleccionar los mensajes que aparecen en la vista mensajes activos.  
  
 [Cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md)  
 Se usa para buscar el nodo de un mensaje específico en la vista mensajes.  
  
 [Cuadro de diálogo Propiedades del mensaje](../debugger/message-properties-dialog-box.md)  
 Se utiliza para mostrar las propiedades de un mensaje seleccionado en la vista de mensajes.  
  
 [Referencia de Spy++](../debugger/spy-increment-reference.md)  
 Incluye secciones que describen cada menú y cuadro de diálogo de Spy + +.
