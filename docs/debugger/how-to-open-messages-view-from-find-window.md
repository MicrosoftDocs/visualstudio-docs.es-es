---
title: 'Cómo: abrir la vista mensajes desde Buscar ventana | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08f832e61bdb39bc87b59fdd64deab8cd86382a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839224"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Cómo: Abrir la vista Mensajes desde Buscar ventana
Le resultará cómodo utilizar el **Buscar ventana** cuadro de diálogo para seleccionar una ventana de destino y, a continuación, abra una vista de mensajes de esa ventana.  

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Para abrir una ventana de vista de mensajes mediante el cuadro de diálogo Buscar ventana  

1. Organizar las ventanas para que estén visibles Spy ++ y la ventana de destino.  

2. Desde el **Spy** menú, elija **Buscar ventana**.  

    El [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md) se abre.  

3. Desde el **Windows** pestaña, arrastre el **herramienta de búsqueda** a través de la ventana de destino. A medida que arrastra la herramienta, el **Buscar ventana** cuadro de diálogo muestra los detalles de la ventana seleccionada.  

   - O  

     Si tiene el identificador de la ventana que desea examinar (por ejemplo, si se copian desde el depurador), puede escribirla en el **controlar** cuadro de texto.  

4. En **mostrar**, seleccione **mensajes**.  

5. Presione **Aceptar**.  

    Un espacio en blanco [vista mensajes](../debugger/messages-view.md) abre la ventana y un **mensajes** menú se agrega a la barra de herramientas de Spy ++.  

6. Desde el **mensajes** menú, elija **opciones de registro**.  

    El [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md) se abre.  

7. Seleccione las opciones para los mensajes que desea mostrar.  

8. Presione **Aceptar** para empezar a mensajes de registro.  

    Dependiendo de las opciones seleccionadas, los mensajes comenzará a transmitir en la ventana activa de la vista de mensajes.  

9. Cuando tenga suficientes mensajes, elija **detener el registro** desde el **mensajes** menú.
