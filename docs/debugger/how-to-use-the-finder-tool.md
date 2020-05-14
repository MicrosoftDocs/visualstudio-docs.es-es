---
title: Procedimiento Uso de la Herramienta de búsqueda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f96fe87137c6b14e32fb2648e93c54a1c5b094a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732164"
---
# <a name="how-to-use-the-finder-tool"></a>Procedimiento Uso de la herramienta de búsqueda
Puede usar la Herramienta de búsqueda del cuadro de diálogo **Buscar ventana** para mostrar las propiedades o los mensajes de una ventana. La Herramienta de búsqueda también puede buscar ventanas secundarias deshabilitadas y decidir qué ventana se va a resaltar si las ventanas secundarias deshabilitadas se superponen.

 ![Cuadro de diálogo Buscar ventana de Spy&#43;&#43;](../debugger/media/icon_spy--_find.png "Icon_Spy++_Find") Herramienta de búsqueda del cuadro de diálogo Buscar ventana

 En la ilustración anterior se muestra el cuadro de diálogo Buscar ventana después del paso 3 siguiente.

### <a name="to-display-window-properties-or-messages"></a>Para mostrar propiedades o mensajes de una ventana

1. Organice las ventanas de modo que se puedan ver la ventana de Spy++ y la ventana de destino.

2. En el menú de **Spy**, seleccione **Buscar ventana**.

    Se abre el [Cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md).

3. Arrastre la **Herramienta de búsqueda** a la ventana de destino.

    Al arrastrar la herramienta, el cuadro de diálogo **Buscar ventana** muestra detalles sobre la ventana seleccionada.

   - O

     Si tiene el identificador de la ventana que quiere examinar (por ejemplo, copiado del depurador), escríbalo en el cuadro de texto **Identificador**.

   > [!TIP]
   > Para despejar la pantalla, seleccione la opción **Ocultar Spy**. Esta opción oculta la ventana principal de Spy++ y deja visible únicamente el cuadro de diálogo **Buscar ventana** encima de las demás aplicaciones. La ventana principal de Spy++ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy++** .

4. En **Mostrar**, seleccione **Propiedades** o **Mensajes**.

5. Haga clic en **Aceptar**.

    Si ha seleccionado **Propiedades**, se abre el [ Cuadro de diálogo Propiedades de la ventana](../debugger/window-properties-dialog-box.md). Si ha seleccionado **Mensajes**, se abre una ventana de la [Vista Mensajes](../debugger/messages-view.md).

## <a name="see-also"></a>Vea también
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)