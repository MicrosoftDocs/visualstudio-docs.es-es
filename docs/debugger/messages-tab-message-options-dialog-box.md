---
title: "Pestaña mensajes, cuadro de diálogo Opciones de mensaje | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c3578db069a90baa8192af0641465dbecc790b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="messages-tab-message-options-dialog-box"></a>Pestaña Mensajes (Cuadro de diálogo Opciones de mensaje)
Use la **mensajes** tab para seleccionar qué tipos de mensaje a la lista en [vista mensajes](../debugger/messages-view.md)así como para especificar criterios de búsqueda del mensaje. Para mostrar la [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **mensajes de registro** desde el **Spy** menú.  
  
 Por lo general, seleccione **grupos de mensajes**y, a continuación, ajustar la selección mediante la selección individual **mensajes a la vista**. El **todos los** botón selecciona todos los tipos de mensaje y el **ninguno** botón borra todos los tipos.  
  
 Las siguientes opciones están disponibles en la **mensajes** ficha:  
  
 **Mensajes a la vista**  
 Seleccione mensajes concretos que desea ver. Cuando se crea una nueva ventana de mensajes, puede mostrar todos los mensajes. Cuando se aplica un filtro a los mensajes desde el **mensajes** ficha, dicho filtro sólo se aplica a los nuevos mensajes, no los mensajes que ya se han mostrado en la vista de Windows.  
  
 **Grupos de mensajes**  
 Seleccione grupos de mensajes para su visualización. Los grupos disponibles son:  
  
-   WM_USER: con un código de mayor o igual que WM_USER  
  
-   Registrado: registrado con el **RegisterWindowMessage** llamar a  
  
-   Desconocido: mensajes desconocidos en el intervalo de 0 a (WM_USER - 1)  
  
 Tenga en cuenta que estos **grupos de mensajes** no se asignan a entradas específicas en **mensajes para ver**. Cuando se selecciona un grupo, la selección se aplica directamente a la secuencia de mensajes.  
  
 Una casilla de verificación sombreada en **grupos de mensajes** indica que la **mensajes para ver** cuadro de lista se ha modificado para los mensajes de ese grupo; no todos los tipos de mensaje de ese grupo están seleccionados.  
  
 **Guardar configuración como predeterminada**  
 Guardar la configuración actual para su posterior uso como opciones de búsqueda de mensajes. Esta configuración también se guarda al salir de Spy ++.