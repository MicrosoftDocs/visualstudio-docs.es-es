---
title: 'Cómo: usar la herramienta de búsqueda | Microsoft Docs'
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732164"
---
# <a name="how-to-use-the-finder-tool"></a>Cómo: Usar la herramienta de búsqueda
Puede usar la herramienta de búsqueda en el cuadro de diálogo **Buscar ventana** para mostrar los mensajes o las propiedades de la ventana. La herramienta de búsqueda también puede buscar ventanas secundarias deshabilitadas y discernir qué ventana se resaltará si las ventanas secundarias deshabilitadas se superponen.

 ![Cuadro&#43; &#43; de diálogo Buscar ventana de Spy](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") Herramienta de búsqueda en el cuadro de diálogo Buscar ventana

 En la ilustración anterior se muestra el cuadro de diálogo Buscar ventana después del paso 3 a continuación.

### <a name="to-display-window-properties-or-messages"></a>Para mostrar los mensajes o las propiedades de la ventana

1. Organice las ventanas de modo que tanto Spy + + como la ventana de destino estén visibles.

2. En el menú **Spy** , elija **Buscar ventana**.

    Se abre el [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md) .

3. Arrastre la **herramienta de búsqueda** sobre la ventana de destino.

    Al arrastrar la herramienta, el cuadro de diálogo **Buscar ventana** muestra detalles en la ventana seleccionada.

   - O

     Si tiene el identificador de la ventana que desea examinar (por ejemplo, copiado desde el depurador), escríbalo en el cuadro de texto **identificador** .

   > [!TIP]
   > Para reducir el desorden de la pantalla, seleccione la opción **ocultar Spy** . Esta opción oculta la ventana principal de Spy + +, mientras que solo el cuadro de diálogo **Buscar ventana** está visible encima de las demás aplicaciones. La ventana principal de Spy + + se restaura al hacer clic en **Aceptar** o en **Cancelar**, o al desactivar la opción **ocultar Spy + +** .

4. En **Mostrar**, seleccione **propiedades** o **mensajes**.

5. Haga clic en **Aceptar**.

    Si seleccionó **propiedades**, se abrirá el [cuadro de diálogo Propiedades](../debugger/window-properties-dialog-box.md) de la ventana. Si seleccionó **mensajes**, se abre una ventana [vista mensajes](../debugger/messages-view.md) .

## <a name="see-also"></a>Vea también
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)