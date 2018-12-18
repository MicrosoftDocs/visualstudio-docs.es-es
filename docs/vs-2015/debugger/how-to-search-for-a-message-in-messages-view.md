---
title: 'Cómo: buscar un mensaje en la vista mensajes | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08a2a08014d0927ecea29b1acb6bb36620f1a15a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802109"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Cómo: Buscar un mensaje en la vista Mensajes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede buscar un mensaje concreto en la vista mensajes mediante su identificador, el tipo o el Id. de mensaje como criterios de búsqueda. Cualquiera de estas, o una combinación, serán los criterios de búsqueda válida. También se puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo se cargan previamente con los atributos del mensaje seleccionado actualmente.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Para buscar un mensaje en la vista mensajes  
  
1. Organizar las ventanas por lo que ese Spy ++ y un activo [vista mensajes](../debugger/messages-view.md) ventana están visibles.  
  
2. Desde el **búsqueda** menú, elija **Buscar mensaje**.  
  
    El [cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md) se abre.  
  
3. Arrastre el **herramienta de búsqueda** a través de la ventana que desee. A medida que arrastra la herramienta, el **Buscar mensaje** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
    -O bien-  
  
    Si tiene el identificador de la ventana cuyos mensajes desea examinar, escríbalo en el **controlar** cuadro de texto.  
  
    -O bien-  
  
    Si conoce el tipo de mensaje o el identificador de mensaje que desee, seleccionarlas desde las **tipo** y **mensaje** menús desplegables y desactive el **controlar** cuadro de texto.  
  
4. Borrar todos los campos que no desea especificar los valores.  
  
   > [!TIP]
   >  Para reducir la confusión en la pantalla, seleccione el **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++, dejando sólo los **Buscar ventana** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.  
  
5. Elija **seguridad** o **abajo** para la dirección inicial de la búsqueda.  
  
6. Haga clic en **Aceptar**.  
  
   Si se encuentra un mensaje coincidente, éste se resalta en la ventana de vista de mensajes. Consulte [la vista mensajes](../debugger/messages-view.md).



