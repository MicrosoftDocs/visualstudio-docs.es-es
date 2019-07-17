---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbe76d800be035bc39caa477955b91bf21c074e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195678"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Usa un motor de depuración (DE) para iniciar y finalizar los programas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante una DE personalizado si tiene requisitos especiales para iniciar un proceso que no se puede controlar completamente por un puerto personalizado. Esto suele ser el caso cuando la DE forma parte de un intérprete y el proceso que se está depurando un script: el intérprete debe iniciarse en primer lugar y, a continuación, se carga e inicia la secuencia de comandos. Un puerto puede iniciar el intérprete, pero la secuencia de comandos puede requerir un tratamiento especial (que es donde la DE tiene un rol). Esta interfaz se implementa solo si hay requisitos únicos para iniciar un programa que no puede controlar un puerto personalizado.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se llama por el Administrador de depuración de la sesión (SDM) si el SDM puede obtener esta interfaz desde el [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (mediante QueryInterface) de la interfaz. Si se puede obtener esta interfaz, el SDM sabe que la DE tiene requisitos especiales y llama a esta interfaz para iniciar el programa en lugar de tener el puerto de iniciarlo.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEngineLaunch2`.  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia un proceso por medio de la DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reanuda la ejecución de procesos.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina si se puede finalizar un proceso.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un proceso.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
