---
title: Pestaña de mensajes, el cuadro de diálogo Opciones de mensaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f7675039f8e5f5fb5c1d5899b96682ab60a2bc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830604"
---
# <a name="messages-tab-message-options-dialog-box"></a>Pestaña Mensajes (Cuadro de diálogo Opciones de mensaje)
Use la **mensajes** tab para seleccionar qué tipos de mensaje a la lista en [vista mensajes](../debugger/messages-view.md)y especificar criterios de búsqueda del mensaje. Para mostrar el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **los mensajes de registro** desde el **Spy** menú.  
  
 Por lo general, seleccione **grupos de mensajes**y, a continuación, ajustar la selección mediante la selección individual **mensajes a la vista**. El **todas** botón selecciona todos los tipos de mensaje y el **ninguno** botón borra todos los tipos.  
  
 Las siguientes opciones están disponibles en el **mensajes** pestaña:  
  
 **Mensajes que se quieren ver**  
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