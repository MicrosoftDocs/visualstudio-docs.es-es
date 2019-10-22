---
title: Procedimiento Utilice la herramienta de búsqueda | Documentos de Microsoft
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
ms.openlocfilehash: 5bf3fcf00486ebb8ec54f2d692d483a7f9cf18d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387654"
---
# <a name="how-to-use-the-finder-tool"></a>Procedimiento Uso de la herramienta de búsqueda
Puede usar la herramienta de búsqueda en el **Buscar ventana** cuadro de diálogo para mostrar la ventana Propiedades o mensajes. La herramienta de búsqueda también puede encontrar ventanas secundarias deshabilitadas y discernir qué ventana resaltar si deshabilita ventanas secundarias se superponen.

 ![Spy&#43; &#43; cuadro de diálogo Buscar ventana](../debugger/media/icon_spy--_find.png "Icon_Spy ++ _Find") herramienta de búsqueda en el cuadro de diálogo Buscar ventana

 La ilustración anterior muestra el cuadro de diálogo Buscar ventana después del paso 3 siguiente.

### <a name="to-display-window-properties-or-messages"></a>Para mostrar la ventana Propiedades o mensajes

1. Organizar las ventanas para que estén visibles Spy ++ y la ventana de destino.

2. Desde el **Spy** menú, elija **Buscar ventana**.

    El [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md) se abre.

3. Arrastre el **herramienta de búsqueda** a través de la ventana de destino.

    A medida que arrastra la herramienta, el **Buscar ventana** cuadro de diálogo muestra los detalles de la ventana seleccionada.

   - O

     Si tiene el identificador de la ventana que desea examinar (por ejemplo, si se copian desde el depurador), escríbalo en el **controlar** cuadro de texto.

   > [!TIP]
   > Para reducir la confusión en la pantalla, seleccione el **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++, dejando sólo los **Buscar ventana** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.

4. En **mostrar**, seleccione **propiedades** o **mensajes**.

5. Haga clic en **Aceptar**.

    Si seleccionó **propiedades**, el [cuadro de diálogo de propiedades de ventana](../debugger/window-properties-dialog-box.md) se abre. Si seleccionó **mensajes**, un [vista mensajes](../debugger/messages-view.md) abre la ventana.

## <a name="see-also"></a>Vea también
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)