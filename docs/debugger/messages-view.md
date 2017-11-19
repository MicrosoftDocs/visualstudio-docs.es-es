---
title: La vista mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools.spyplus.messagesview
helpviewer_keywords: Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 538cd0cd023b8861d6adb88c19b42aac59c9f4dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="messages-view"></a>Vista Mensajes
Cada ventana tiene una secuencia de mensaje asociado. Esta secuencia de mensajes muestra en una ventana de vista de mensajes. Se muestran el identificador de ventana, el código de mensaje y el mensaje. Puede crear una vista de mensajes para un subproceso o proceso también. Esto permite ver los mensajes enviados a todas las ventanas que pertenecen a un proceso o subproceso concreto, que es especialmente útil para capturar mensajes de inicialización de la ventana.  
  
 Una ventana de vista mensajes típica aparece debajo. Tenga en cuenta que la primera columna contiene el identificador de ventana y la segunda columna contiene un código de mensaje (explicado en [códigos de mensaje](../debugger/message-codes.md)). Parámetros de mensaje descodificados y valores devueltos son de la derecha.  
  
 ![Spy &#43; &#43; La vista mensajes](../debugger/media/spy--_messagesview.png "Spy ++ _MessagesView")  
Vista de mensajes de Spy++  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Para abrir una vista mensajes para una ventana, proceso o subproceso  
  
1.  Mover el foco a un [Windows Vista](../debugger/windows-view.md), [vista procesos](../debugger/processes-view.md), o [vista de subprocesos](../debugger/threads-view.md) ventana.  
  
2.  Busque el nodo para el elemento cuyos mensajes desea examinar y selecciónelo.  
  
3.  Desde el **Spy** menú, elija **mensajes de registro**.  
  
     El [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) se abre.  
  
4.  Seleccione las opciones para el mensaje que desea mostrar.  
  
5.  Presione **Aceptar** para empezar a registrar mensajes.  
  
     Un mensajes abre la ventana de vista y un **mensajes** menú se agrega a la barra de herramientas de Spy ++. Dependiendo de las opciones seleccionadas, mensajes de empezar a transmitir en la ventana de vista mensajes activa.  
  
6.  Cuando haya suficientes mensajes, elija **detener el registro** desde el **mensajes** menú.  
  
## <a name="in-this-section"></a>En esta sección  
 [Controlar la vista mensajes](../debugger/how-to-control-messages-view.md)  
 Explica cómo administrar la vista mensajes.  
  
 [Abrir la vista mensajes desde Buscar ventana](../debugger/how-to-open-messages-view-from-find-window.md)  
 Explica cómo abrir la vista mensajes desde el cuadro de diálogo Buscar ventana.  
  
 [Buscar un mensaje en la vista mensajes](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Explica cómo encontrar un mensaje concreto en la vista de mensajes.  
  
 [Iniciar y detener la presentación del registro de mensaje](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Explica cómo iniciar y detener el registro de mensajes.  
  
 [Códigos de mensaje](../debugger/message-codes.md)  
 Define los códigos para los mensajes que aparecen en la vista de mensajes.  
  
 [Mostrar propiedades de mensaje](../debugger/how-to-display-message-properties.md)  
 Cómo mostrar más información acerca de un mensaje.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Vistas de Spy++](../debugger/spy-increment-views.md)  
 Explica las vistas de árbol de Spy ++ de ventanas, mensajes, procesos y subprocesos.  
  
 [Usar Spy++](../debugger/using-spy-increment.md)  
 Presenta la herramienta Spy ++ y explica cómo se puede usar.  
  
 [Cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md)  
 Se usa para seleccionar qué mensajes se muestran en la vista activa de mensajes.  
  
 [Cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md)  
 Se usa para encontrar el nodo de un mensaje concreto en la vista mensajes.  
  
 [Cuadro de diálogo Propiedades del mensaje](../debugger/message-properties-dialog-box.md)  
 Se utiliza para mostrar las propiedades de un mensaje seleccionado en la vista mensajes.  
  
 [Referencia de Spy++](../debugger/spy-increment-reference.md)  
 Incluye secciones que describen cada Spy ++ menú y cuadro de diálogo.