---
title: IDebugEngineLaunch2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2
helpviewer_keywords: IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 989bea1fc3398be376c7c2d5c41ce390e59c228f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Usado por un motor de depuración (Alemania) para iniciar y finalizar programas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante un Alemania personalizado si tiene requisitos especiales para iniciar un proceso que no se pueden administrar completamente con un puerto personalizado. Esto suele ser el caso cuando la DE forma parte de un intérprete y el proceso que se está depurando un script: el intérprete debe iniciarse en primer lugar y, a continuación, se carga y se inicia la secuencia de comandos. Un puerto puede iniciar el intérprete, pero la secuencia de comandos puede requerir un tratamiento especial (que es donde el Alemania tiene un rol). Esta interfaz se implementa solo si hay requisitos únicos para iniciar un programa que no puede controlar un puerto personalizado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se invoca mediante el Administrador de sesión de depuración (SDM) si el SDM puede obtener esta interfaz desde el [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (mediante QueryInterface) de la interfaz. Si esta interfaz puede obtenerse el SDM sabe que la DE tiene requisitos especiales y llama a esta interfaz para iniciar el programa en lugar de tener el puerto de iniciarla.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEngineLaunch2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia un proceso por medio de la DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reanuda la ejecución de procesos.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina si se puede finalizar un proceso.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un proceso.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)