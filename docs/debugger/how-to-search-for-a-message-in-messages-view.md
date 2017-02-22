---
title: "How to: Search for a Message in Messages View | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Message Search dialog box"
  - "Messages view"
  - "messages, searching for"
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Message in Messages View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para buscar un mensaje concreto en la vista Mensajes se puede usar su identificador, su tipo o su identificador de mensaje como criterios de búsqueda.  Cualquiera de éstos, de forma individual o combinada, serán criterios de búsqueda válidos.  También se puede especificar la dirección inicial de la búsqueda.  Los campos del cuadro de diálogo se cargan previamente con los atributos del mensaje actualmente seleccionado.  
  
### Para buscar un mensaje en la vista Mensajes  
  
1.  Organice las ventanas de modo que estén visibles la ventana de Spy\+\+ y una ventana de [vista Mensajes](../debugger/messages-view.md) activa.  
  
2.  En el menú **Buscar**, elija **Buscar mensaje**.  
  
     Se abrirá el [cuadro de diálogo Buscar mensaje](../debugger/message-search-dialog-box.md).  
  
3.  Arrastre la **herramienta de búsqueda** sobre la ventana que desee.  Mientras se arrastra la herramienta, el cuadro de diálogo **Buscar mensaje** muestra los detalles de la ventana seleccionada.  
  
     \-O bien\-  
  
     Si tiene el identificador de la ventana cuyos mensajes desea examinar, escríbalo en el cuadro de texto **Identificador**.  
  
     \-O bien\-  
  
     Si conoce el tipo de mensaje o el identificador de mensaje, selecciónelos en los menús desplegables **Tipo** y **Mensaje**, y borre el cuadro de texto **Identificador**.  
  
4.  Borre cualquier campo para el que no desee especificar valores.  
  
    > [!TIP]
    >  Para reducir el desorden de la pantalla, seleccione la opción **Ocultar Spy\+\+**.  Esta opción oculta la ventana principal de Spy\+\+ y deja únicamente el cuadro de diálogo **Buscar ventana** visible encima de las demás aplicaciones.  La ventana principal de Spy\+\+ se restaura al hacer clic en **Aceptar** o **Cancelar**, o al desactivar la opción **Ocultar Spy\+\+**.  
  
5.  Elija **Arriba** o **Abajo** como dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un mensaje coincidente, se resalta en la ventana de la vista Mensajes.  Vea [Vista Mensajes](../debugger/messages-view.md).