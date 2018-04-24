---
title: 'Cómo: buscar un mensaje en la vista mensajes | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368d10f2285c94f053e536da77966e9b2fb26da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Cómo: Buscar un mensaje en la vista Mensajes
Puede buscar un mensaje concreto en la vista mensajes mediante su identificador, el tipo o el Id. de mensaje como criterios de búsqueda. Cualquiera de estos, o una combinación, serán criterios de búsqueda válido. También se puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo se cargan previamente con los atributos del mensaje actualmente seleccionado.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Para buscar un mensaje en la vista mensajes  
  
1.  Organizar las ventanas de modo que ese Spy ++ y cuando se activa [vista mensajes](../debugger/messages-view.md) ventana están visibles.  
  
2.  Desde el **búsqueda** menú, elija **Buscar mensaje**.  
  
     El [cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md) se abre.  
  
3.  Arrastre el **herramienta de búsqueda** sobre la ventana deseada. A medida que arrastra la herramienta, el **Buscar mensaje** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
     - O  
  
     Si tiene el identificador de la ventana cuyos mensajes desea examinar, escríbalo en el **controlar** cuadro de texto.  
  
     - O  
  
     Si conoce el tipo de mensaje o el identificador de mensaje que desea, selecciónelos desde el **tipo** y **mensaje** menús desplegables y desactive el **controlar** cuadro de texto.  
  
4.  Desactive los campos para los que no desea especificar los valores.  
  
    > [!TIP]
    >  Para reducir la acumulación de elementos de pantalla, seleccione la **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++, dejando sólo los **Buscar ventana** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.  
  
5.  Elija **una** o **hacia abajo** para la dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un mensaje coincidente, se resalta en la ventana de vista de mensajes. Vea [la vista mensajes](../debugger/messages-view.md).