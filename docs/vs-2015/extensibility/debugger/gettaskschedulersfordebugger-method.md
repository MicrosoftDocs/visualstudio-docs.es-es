---
title: GetTaskSchedulersForDebugger (método) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d2bc798575cafbeb04837c3065d69b76ee872df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576704"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (Método)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [GetTaskSchedulersForDebugger (método)](https://docs.microsoft.com/visualstudio/extensibility/debugger/gettaskschedulersfordebugger-method).  
  
Recupera una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están activos actualmente.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Una matriz de todos los <xref:System.Threading.Tasks.TaskScheduler> objetos que están actualmente activos en este <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Comentarios  
 Este método no es seguro para subprocesos y no deben usarse simultáneamente con otras instancias de <xref:System.Threading.Tasks.TaskScheduler>. Debe llamarse desde un depurador sólo cuando el depurador ha suspendido todos los demás subprocesos.  
  
## <a name="see-also"></a>Vea también  
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)

