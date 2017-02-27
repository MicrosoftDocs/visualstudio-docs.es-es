---
title: "SetNotificationForWaitCompletion (m&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Método de SetNotificationForWaitCompletion, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# SetNotificationForWaitCompletion (m&#233;todo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece o borra el bit de estado TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
## Sintaxis  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### Parámetros  
 `enabled`  
  
 `true` Para establecer el bit; `false` a sin establecer el bit.  
  
## Excepciones  
  
## Comentarios  
 El depurador establece este bit para ayudar a paso para salir de un cuerpo de método asincrónico. Si `enabled` es `true`, debe llamar a este método solo en una tarea que aún no se ha completado. Si `enabled` es `false`, puede llamar a este método en las tareas completadas. En cualquier caso, sólo debe utilizarse para tareas de estilo promesa.  
  
## Requisitos  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)