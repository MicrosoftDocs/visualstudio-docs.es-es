---
title: Procedimiento Búsqueda de una ventana en la vista Ventanas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba5c8469885fd62c99a672e894cde82700c980d
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64831029"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Procedimiento Búsqueda de una ventana en la vista Ventanas
Puede buscar una ventana específica en la vista Ventanas mediante su identificador, título o clase, o una combinación de su título y clase, como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. En los campos del cuadro de diálogo se mostrarán los atributos de la ventana seleccionada en el árbol de ventanas.

 Comience por el árbol expandido al segundo nivel (todas las ventanas que son elementos secundarios del escritorio), para que pueda identificar las ventanas del escritorio por su nombre de clase y título. Una vez que haya elegido una ventana del escritorio, puede expandir ese nivel para buscar una ventana secundaria concreta.

### <a name="to-search-for-a-window-in-windows-view"></a>Para buscar una ventana en la vista Ventanas

1. Organice las ventanas para que se puedan ver las de Spy++, la de la [vista Ventanas](../debugger/windows-view.md) y la de destino.

2. En el menú **Buscar**, seleccione **Buscar ventana**.

    Se abrirá el cuadro de diálogo [Buscar ventana](../debugger/window-search-dialog-box.md).

   > [!TIP]
   > Para reducir el desorden de la pantalla, seleccione la opción **Ocultar Spy**. Esta opción oculta la ventana principal de Spy++ y deja visible únicamente el cuadro de diálogo **Buscar ventana** encima de las otras aplicaciones. La ventana principal de Spy++ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy++** .

3. Arrastre la **Herramienta de búsqueda** sobre la ventana de destino. Al arrastrar la herramienta, el cuadro de diálogo **Buscar ventana** muestra detalles sobre la ventana seleccionada.

   - O

     Si conoce el identificador de la ventana que le interesa (por ejemplo, del depurador), puede escribirlo en el cuadro **Identificador**.

   - O

     Si conoce el título o la clase de la ventana que le interesa, puede escribirlos en los cuadros de texto **Título** y **Clase**, y desactivar el cuadro de texto **Identificador**.

4. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.

5. Haga clic en **Aceptar**.

    Si se encuentra una ventana coincidente, se resaltará en la ventana [vista Ventanas](../debugger/windows-view.md).