---
title: "Message Codes | Microsoft Docs"
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
  - "message codes"
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Message Codes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cada línea de mensajes que aparece en la [vista Mensajes](../debugger/messages-view.md) contiene un código "P", "S", "s" o "R".  Estos códigos tienen los significados siguientes:  
  
|Código|Significado|  
|------------|-----------------|  
|P|El mensaje se envió a la cola con la función **PostMessage**.  No se dispone de información sobre la distribución final del mensaje.|  
|S|El mensaje se envió con la función **SendMessage**.  Esto significa que el remitente no recobra el control hasta que el receptor procese y devuelva el mensaje.  Por consiguiente, el receptor puede pasar un valor devuelto al remitente.|  
|s|Se envió el mensaje, pero, por motivos de seguridad, no se tiene acceso al valor devuelto.|  
|R|Cada línea "S" tiene su correspondiente línea "R" que muestra el valor devuelto del mensaje.  A veces las llamadas de mensajes están anidadas, lo que significa que un controlador de mensajes envía otro mensaje.|