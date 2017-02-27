---
title: "m_stateObject campo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "campo m_stateObject, clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# m_stateObject campo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Objeto que representa los datos que se va a utilizar la acción.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## Comentarios  
 Se trata de la `state` parámetro en el <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo para la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)