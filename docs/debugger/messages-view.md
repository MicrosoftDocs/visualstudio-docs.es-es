---
title: La vista mensajes | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b20ed28518c9156e82c6fe75ecceda74c66615d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845862"
---
# <a name="messages-view"></a>Vista Mensajes
Cada ventana tiene una secuencia de mensaje asociado. Una ventana de vista de mensajes muestra esta secuencia de mensajes. Se muestran el identificador de ventana, el código de mensaje y el mensaje. Puede crear una vista de mensajes para un subproceso o proceso también. Esto le permite ver los mensajes enviados a todas las ventanas que pertenecen a un proceso o subproceso específico, que es especialmente útil para capturar mensajes de inicialización de la ventana.

 Aparece una ventana de vista típica de los mensajes a continuación. Tenga en cuenta que la primera columna contiene el identificador de ventana y la segunda columna contiene un código de mensaje (se explica en [códigos de mensaje](../debugger/message-codes.md)). Parámetros de mensaje descodificado y valores devueltos aparecen a la derecha.

 ![Spy&#43; &#43; la vista mensajes](../debugger/media/spy--_messagesview.png "Spy ++ _MessagesView") vista mensajes de Spy ++

## <a name="procedures"></a>Procedimientos

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Para abrir una vista de mensajes de ventana, proceso o subproceso

1. Mover el foco a un [Windows Vista](../debugger/windows-view.md), [vista procesos](../debugger/processes-view.md), o [vista de subprocesos](../debugger/threads-view.md) ventana.

2. Busque el nodo para el elemento cuyos mensajes que desea examinar y selecciónelo.

3. Desde el **Spy** menú, elija **los mensajes de registro**.

     El [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) se abre.

4. Seleccione las opciones para el mensaje que desea mostrar.

5. Presione **Aceptar** para empezar a mensajes de registro.

     Una mensajes que se abre la ventana de vista y un **mensajes** menú se agrega a la barra de herramientas de Spy ++. Dependiendo de las opciones seleccionadas, los mensajes comenzará a transmitir en la ventana activa de la vista de mensajes.

6. Cuando tenga suficientes mensajes, elija **detener el registro** desde el **mensajes** menú.

## <a name="in-this-section"></a>En esta sección
 [Controlar la vista mensajes](../debugger/how-to-control-messages-view.md) se explica cómo administrar la vista de mensajes.

 [Abrir vista mensajes desde Buscar ventana](../debugger/how-to-open-messages-view-from-find-window.md) se explica cómo abrir la vista mensajes desde el cuadro de diálogo Buscar ventana.

 [Buscar un mensaje en la vista mensajes](../debugger/how-to-search-for-a-message-in-messages-view.md) se explica cómo encontrar un mensaje concreto en la vista mensajes.

 [Iniciar y detener la presentación del mensaje de registro](../debugger/how-to-start-and-stop-the-message-log-display.md) se explica cómo iniciar y detener el registro de mensajes.

 [Códigos de mensaje](../debugger/message-codes.md) define los códigos para los mensajes se muestran en la vista mensajes.

 [Mostrar las propiedades de mensaje](../debugger/how-to-display-message-properties.md) cómo mostrar más información acerca de un mensaje.

## <a name="related-sections"></a>Secciones relacionadas
 [Vistas de Spy ++](../debugger/spy-increment-views.md) explica las vistas de árbol de Spy ++ de windows, los mensajes, los procesos y subprocesos.

 [Usar Spy ++](../debugger/using-spy-increment.md) presenta la herramienta Spy ++ y explica cómo se puede usar.

 [Cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) utiliza para seleccionar qué mensajes se muestran en la vista activa de mensajes.

 [Cuadro de diálogo de búsqueda del mensaje](../debugger/message-search-dialog-box.md) usa para encontrar el nodo de un mensaje concreto en la vista mensajes.

 [Cuadro de diálogo Propiedades del mensaje](../debugger/message-properties-dialog-box.md) utilizado para mostrar las propiedades de un mensaje seleccionado en la vista de mensajes.

 [Referencia de Spy ++](../debugger/spy-increment-reference.md) incluye secciones que describen cada Spy ++ menú y cuadro de diálogo.