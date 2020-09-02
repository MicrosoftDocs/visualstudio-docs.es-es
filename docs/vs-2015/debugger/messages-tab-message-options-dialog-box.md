---
title: Pestaña Mensajes, (Cuadro de diálogo Opciones de mensaje) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149438"
---
# <a name="messages-tab-message-options-dialog-box"></a>Pestaña Mensajes (Cuadro de diálogo Opciones de mensaje)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **Mensajes** para seleccionar los tipos de mensaje que se van a mostrar en la [vista Mensajes](../debugger/messages-view.md) y para especificar los criterios de búsqueda de mensajes. Para mostrar el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **Mensajes de registro** en el menú de **Spy**.  
  
 Normalmente, primero se selecciona **Grupos de mensajes** y, después, se ajusta mediante la selección de **Mensajes que se quieren ver** individuales. El botón **Todos** selecciona todos los tipos de mensaje y el botón **Ninguno** los borra todos.  
  
 En la pestaña **Mensajes** están disponibles los valores siguientes:  
  
 **Mensajes que se quieren ver**  
 Seleccione mensajes específicos para su visualización. Al crear una ventana Mensajes, se pueden mostrar todos los mensajes. Al filtrar los mensajes desde la pestaña **Mensajes**, ese filtro solo se aplica a los mensajes nuevos, no a los que ya se han mostrado en la vista Ventanas.  
  
 **Grupos de mensajes**  
 Seleccione los grupos de mensajes que se van a ver. Los grupos disponibles son los siguientes:  
  
- WM_USER: con un código mayor o igual que WM_USER  
  
- Registrado: registrado con la llamada a **RegisterWindowMessage**  
  
- Desconocido: mensajes desconocidos en el intervalo de 0 a (WM_USER-1)  
  
  Tenga en cuenta que estos **Grupos de mensajes** no se asignan a entradas específicas de **Mensajes que se quieren ver**. Al seleccionar un grupo, la selección se aplica directamente a la secuencia de mensajes.  
  
  Una casilla atenuada dentro de **Grupos de mensajes** indica que el cuadro de lista **Mensajes que se quieren ver** se ha modificado para los mensajes de ese grupo; no se seleccionan todos los tipos de mensaje de ese grupo.  
  
  **Guardar configuración como predeterminada**  
  Guarde la configuración actual para usarla más adelante como opciones de búsqueda de mensajes. Esta configuración también se guarda al salir de Spy++.
