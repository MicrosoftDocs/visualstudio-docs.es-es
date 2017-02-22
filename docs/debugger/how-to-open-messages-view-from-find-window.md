---
title: "C&#243;mo: Abrir la vista Mensajes desde Buscar ventana | Microsoft Docs"
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
  - "Vista Mensajes de Spy++, abrir"
  - "abrir Vista Mensajes de Spy++"
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Abrir la vista Mensajes desde Buscar ventana
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quizás le resulte cómodo usar el cuadro de diálogo **Buscar ventana** para seleccionar una ventana de destino y, a continuación, abrir una vista Mensajes de esa ventana.  
  
### Para abrir una ventana de vista Mensajes mediante el cuadro de diálogo Buscar ventana  
  
1.  Organice las ventanas de modo que estén visibles Spy\+\+ y la ventana de destino.  
  
2.  En el menú **Spy**, elija **Buscar ventana**.  
  
     Se abrirá el [cuadro de diálogo Buscar ventana](../debugger/find-window-dialog-box.md).  
  
3.  En la pestaña **Ventanas**, arrastre la **herramienta de búsqueda** sobre la ventana de destino.  Mientras se arrastra la herramienta, el cuadro de diálogo **Buscar ventana** muestra los detalles de la ventana seleccionada.  
  
     \-O bien\-  
  
     Si tiene el identificador de la ventana que desea examinar \(por ejemplo, lo copió del depurador\), puede escribirlo en el cuadro de texto **Identificador**.  
  
4.  En **Mostrar**, seleccione **Mensajes**.  
  
5.  Presione **Aceptar**.  
  
     Se abrirá una ventana de [vista Mensajes](../debugger/messages-view.md) en blanco y se agregará un menú **Mensajes** a la barra de herramientas de Spy\+\+.  
  
6.  En el menú **Mensajes**, elija **Opciones de registro**.  
  
     Se abrirá el [cuadro de diálogo Opciones de mensaje](../debugger/message-options-dialog-box.md).  
  
7.  Seleccione las opciones de los mensajes que desea mostrar.  
  
8.  Presione **Aceptar** para empezar a registrar mensajes.  
  
     Dependiendo de las opciones seleccionadas, se empezarán a transmitir por secuencias mensajes a la ventana de vista Mensajes activa.  
  
9. Cuando tenga suficientes mensajes, elija **Detener el registro** en el menú **Mensajes**.