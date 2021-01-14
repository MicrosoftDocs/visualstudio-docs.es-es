---
title: Apertura de una vista Mensajes desde Buscar ventana | Microsoft Docs
description: Use el cuadro de diálogo Buscar ventana en Spy++ para seleccionar una ventana de destino y, luego, abrir una vista Mensajes para esa ventana.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e66e3e1200e1e08776853f2ac8308537e4b4a17
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148915"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Procedimiento Apertura de la vista Mensajes desde la ventana Buscar
Es posible que le resulte cómodo usar el cuadro de diálogo **Buscar ventana** para seleccionar una ventana de destino y luego abrir una vista Mensajes de esa ventana.

### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Para abrir una ventana de una vista Mensajes mediante el cuadro de diálogo Buscar ventana

1. Organice las ventanas de modo que se puedan ver la ventana de Spy++ y la ventana de destino.

2. En el menú de **Spy**, seleccione **Buscar ventana**.

    Se abre el [Cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md).

3. En la pestaña **Ventanas**, arrastre la **Herramienta de búsqueda** a la ventana de destino. Al arrastrar la herramienta, el cuadro de diálogo **Buscar ventana** muestra detalles sobre la ventana seleccionada.

   - O

     Si tiene el identificador de la ventana que quiere examinar (por ejemplo, copiado del depurador), puede escribirlo en el cuadro de texto **Identificador**.

4. En **Mostrar**, seleccione **Mensajes**.

5. Haga clic en **Aceptar**.

    Se abre una ventana en blanco de una [Vista Mensajes](../debugger/messages-view.md) y se agrega un menú **Mensajes** a la barra de herramientas de Spy++.

6. En el menú **Mensajes**, seleccione **Opciones de registro**.

    Se abre el [Cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md).

7. Seleccione las opciones de los mensajes que quiere mostrar.

8. Presione **Aceptar** para empezar a registrar mensajes.

    En función de las opciones seleccionadas, los mensajes comienzan a transmitirse a la ventana de la vista Mensajes activa.

9. Cuando tenga suficientes mensajes, seleccione **Detener registro** en el menú **Mensajes**.
