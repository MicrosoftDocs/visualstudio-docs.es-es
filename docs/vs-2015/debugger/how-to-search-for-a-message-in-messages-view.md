---
title: Procedimiento Búsqueda de un mensaje en la vista Mensajes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c89a763389abe364fe70166e63b41f932581837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842426"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Procedimiento Búsqueda de un mensaje en la vista Mensajes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar un mensaje específico en la vista Mensajes mediante su manipulador, tipo o identificador de mensaje como criterios de búsqueda. Cualquiera de ellos (o una combinación) será un criterio de búsqueda válido. También se puede especificar la dirección inicial de la búsqueda. Los campos del cuadro de diálogo se cargan previamente con los atributos del mensaje seleccionado actualmente.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Búsqueda de un mensaje en la vista Mensajes  
  
1. Organice las ventanas para que se vea la ventana de Spy++ y una ventana activa de la [vista Mensajes](../debugger/messages-view.md).  
  
2. En el menú **Buscar**, seleccione **Buscar mensaje**.  
  
    Se abre el [cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md).  
  
3. Arrastre la **Herramienta de búsqueda** a la ventana de destino. Al arrastrar la herramienta, el cuadro de diálogo **Buscar mensaje** muestra detalles sobre la ventana seleccionada.  
  
    -O bien-  
  
    Si tiene el manipulador de la ventana cuyos mensajes quiere examinar, escríbalo en el cuadro de texto **Manipulador**.  
  
    -O bien-  
  
    Si conoce el tipo de mensaje o el identificador de mensaje que quiere, selecciónelos en los menús desplegables **Tipo** y **Mensaje** y borre el cuadro de texto **Manipulador**.  
  
4. Borre los campos en los que no quiera especificar ningún valor.  
  
   > [!TIP]
   > Para despejar la pantalla, seleccione la opción **Ocultar Spy**. Esta opción oculta la ventana principal de Spy++ y deja visible únicamente el cuadro de diálogo **Buscar ventana** encima de las demás aplicaciones. La ventana principal de Spy++ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy++** .  
  
5. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.  
  
6. Haga clic en **Aceptar**.  
  
   Si se encuentra un mensaje coincidente, se resalta en la ventana de la vista Mensajes. Vea [Vista Mensajes](../debugger/messages-view.md).
