---
title: "GetTaskSchedulersForDebugger (m&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Método de GetTaskSchedulersForDebugger, clase de TaskScheduler [motores de depuración de .NET Framework]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetTaskSchedulersForDebugger (m&#233;todo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 Porque no se puede tener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## Valor devuelto  
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están actualmente activos en <xref:System.AppDomain>.  
  
## Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Se debe llamar desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.  
  
## Vea también  
 [TaskScheduler \(clase\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)