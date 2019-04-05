---
title: 'TaskScheduler Class: miembros internos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995668"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler (Clase): miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este tema se describe los miembros internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase que le ayudarán a implementar un depurador personalizado. Para obtener información general acerca de esta clase, vea el <xref:System.Threading.Tasks.TaskScheduler> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matriz de todas las tareas programadas.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
