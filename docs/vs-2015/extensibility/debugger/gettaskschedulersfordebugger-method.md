---
title: Método GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152723"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente en este objeto <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no debe usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler> . Solo se debe llamar desde un depurador cuando el depurador ha suspendido todos los demás subprocesos.  
  
## <a name="see-also"></a>Consulte también  
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
