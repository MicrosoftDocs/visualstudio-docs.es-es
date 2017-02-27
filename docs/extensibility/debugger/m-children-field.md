---
title: "m_children campo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "campo de m_children, ContingentProperties clase [motores de depuración de .NET Framework]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# m_children campo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La lista de tareas secundarias que están registrados en esta tarea.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## Comentarios  
 Mientras se ejecuta la tarea, sólo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.  
  
 Si la tarea se ha completado, otros subprocesos pueden tener acceso a este campo siempre y cuando no se agrega nada a ella ni eliminar nada de ella.  
  
## Vea también  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)