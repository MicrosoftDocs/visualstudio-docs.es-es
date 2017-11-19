---
title: "Método GetTaskSchedulersForDebugger | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 474d809f36d21b254dbb8bf302cd21bc83db88a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (método)
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están actualmente activos en esta <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Debe llamarse desde un depurador solo cuando el depurador suspende todos los demás subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Clase de objeto TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)