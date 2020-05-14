---
title: Procedimiento Búsqueda de un mensaje en la vista Mensajes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f99c30c23461ada406bb0650f86d45d2a4a2e9
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64832461"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedimiento Búsqueda de un mensaje en la vista Mensajes
Puede buscar un mensaje específico en la vista Mensajes mediante su manipulador, tipo o identificador de mensaje como criterios de búsqueda. Cualquiera de ellos (o una combinación) será un criterio de búsqueda válido. También se puede especificar la dirección inicial de la búsqueda. Los campos del cuadro de diálogo se cargan previamente con los atributos del mensaje seleccionado actualmente.

### <a name="to-search-for-a-message-in-messages-view"></a>Búsqueda de un mensaje en la vista Mensajes

1. Organice las ventanas para que se vea la ventana de Spy++ y una ventana activa de la [vista Mensajes](../debugger/messages-view.md).

2. En el menú **Buscar**, seleccione **Buscar mensaje**.

    Se abre el [cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md).

3. Arrastre la **Herramienta de búsqueda** a la ventana de destino. Al arrastrar la herramienta, el cuadro de diálogo **Buscar mensaje** muestra detalles sobre la ventana seleccionada.

   - O

     Si tiene el manipulador de la ventana cuyos mensajes quiere examinar, escríbalo en el cuadro de texto **Manipulador**.

   - O

     Si conoce el tipo de mensaje o el identificador de mensaje que quiere, selecciónelos en los menús desplegables **Tipo** y **Mensaje** y borre el cuadro de texto **Manipulador**.

4. Borre los campos en los que no quiera especificar ningún valor.

   > [!TIP]
   > Para despejar la pantalla, seleccione la opción **Ocultar Spy**. Esta opción oculta la ventana principal de Spy++ y deja visible únicamente el cuadro de diálogo **Buscar ventana** encima de las demás aplicaciones. La ventana principal de Spy++ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy++** .

5. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.

6. Haga clic en **Aceptar**.

   Si se encuentra un mensaje coincidente, se resalta en la ventana de la vista Mensajes. Vea [Vista Mensajes](../debugger/messages-view.md).