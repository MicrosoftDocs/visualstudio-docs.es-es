---
title: "Pesta&#241;a Mensajes (Cuadro de di&#225;logo Opciones de mensaje) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opciones de mensaje, mensajes"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Pesta&#241;a Mensajes (Cuadro de di&#225;logo Opciones de mensaje)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la pestaña **Mensajes** para seleccionar qué tipos de mensaje desea mostrar en la [vista Mensajes](../debugger/messages-view.md) y para especificar los criterios de búsqueda de mensajes.  Para abrir el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md), elija **Mensajes de registro** en el menú **Spy**.  
  
 Normalmente, primero se selecciona **Grupos de mensajes** y, a continuación, se limita la selección mediante **Mensajes que se desean ver**.  El botón **Todo** selecciona todos los tipos de mensaje y el botón **Ninguno** anula la selección de todos los tipos.  
  
 En la pestaña **Mensajes** está disponible la configuración siguiente:  
  
 **Mensajes que se desean ver**  
 Seleccione los mensajes que desea ver en concreto.  Cuando se crea una nueva ventana Mensajes, puede mostrar todos los mensajes.  Al filtrar los mensajes en la pestaña **Mensajes**, el filtro sólo se aplica a los nuevos mensajes, no a los mensajes ya mostrados en la vista Ventanas.  
  
 **Grupos de mensajes**  
 Seleccione los grupos de mensajes que desea ver.  Los grupos disponibles son:  
  
-   WM\_USER: con un código mayor o igual que WM\_USER  
  
-   Registrado: registrado con la llamada **RegisterWindowMessage**  
  
-   Desconocido: mensajes desconocidos en el intervalo de 0 a \(WM\_USER – 1\)  
  
 Observe que estos **grupos de mensajes** no están asignados a entradas concretas en **Mensajes que se desean ver**.  Al seleccionar un grupo, la selección se aplica directamente a la secuencia de mensajes.  
  
 Si hay una casilla deshabilitada en **Grupos de mensajes**, significa que el cuadro de lista **Mensajes que se desean ver** se ha modificado para los mensajes de ese grupo; no todos los tipos de mensaje de ese grupo están seleccionados.  
  
 **Guardar configuración como predeterminada**  
 Guarda la configuración actual para su posterior uso como opciones de búsqueda de mensajes.  Esta configuración también se guarda al salir de Spy\+\+.