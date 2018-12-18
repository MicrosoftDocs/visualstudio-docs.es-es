---
title: Pestaña de mensajes, el cuadro de diálogo Opciones de mensaje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 55906da398f7f52460523cb74a77945d84037ebc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866771"
---
# <a name="messages-tab-message-options-dialog-box"></a>Pestaña Mensajes (Cuadro de diálogo Opciones de mensaje)
Use la **mensajes** tab para seleccionar qué tipos de mensaje a la lista en [vista mensajes](../debugger/messages-view.md)y especificar criterios de búsqueda del mensaje. Para mostrar el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **los mensajes de registro** desde el **Spy** menú.  
  
 Por lo general, seleccione **grupos de mensajes**y, a continuación, ajustar la selección mediante la selección individual **mensajes a la vista**. El **todas** botón selecciona todos los tipos de mensaje y el **ninguno** botón borra todos los tipos.  
  
 Las siguientes opciones están disponibles en el **mensajes** pestaña:  
  
 **Mensajes a la vista**  
 Seleccione mensajes específicos para su visualización. Cuando se crea una nueva ventana de mensajes, puede mostrar todos los mensajes. Cuando se filtra los mensajes de la **mensajes** ficha, dicho filtro sólo se aplica a los nuevos mensajes, no de los mensajes que ya se han mostrado en la vista de Windows.  
  
 **Grupos de mensajes**  
 Seleccione los grupos de mensajes para su visualización. Los grupos disponibles incluyen:  
  
- WM_USER: con un código de mayor o igual que WM_USER  
  
- Registrado: registrado con el **RegisterWindowMessage** llamar  
  
- Desconocido: mensajes desconocidos en el intervalo de 0 a (WM_USER - 1)  
  
  Tenga en cuenta que estos **grupos de mensajes** no se asignan a entradas específicas de **mensajes para ver**. Cuando se selecciona un grupo, la selección se aplica directamente a la secuencia de mensajes.  
  
  Una casilla deshabilitada en **grupos de mensajes** indica que el **mensajes para ver** cuadro de lista se ha modificado para los mensajes de ese grupo; no todos los tipos de mensaje de ese grupo están seleccionados.  
  
  **Guardar configuración como predeterminada**  
  Guardar la configuración actual para su uso posterior como opciones de búsqueda de mensajes. Esta configuración también se guarda al salir de Spy ++.