---
title: IDebugEngineLaunch2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730495"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilizado por un motor de depuración (DE) para iniciar y terminar programas.

## <a name="syntax"></a>Sintaxis

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un DE personalizado si tiene requisitos especiales para iniciar un proceso que no se puede controlar por completo mediante un puerto personalizado. Este suele ser el caso cuando el DE forma parte de un intérprete y el proceso que se está depurando es un script: el intérprete debe iniciarse primero y, a continuación, se carga e inicia el script. Un puerto puede iniciar el intérprete, pero el script puede requerir un control especial (que es donde la DE tiene un rol). Esta interfaz solo se implementa si hay requisitos únicos para iniciar un programa que un puerto personalizado no puede controlar.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El administrador de depuración de sesión (SDM) llama a esta interfaz si el SDM puede obtener esta interfaz desde la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (mediante QueryInterface). Si se puede obtener esta interfaz, el SDM sabe que el DE tiene requisitos especiales y llama a esta interfaz para iniciar el programa en lugar de hacer que el puerto lo inicie.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEngineLaunch2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia un proceso a través del DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reanuda la ejecución del proceso.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina si se puede finalizar un proceso.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Finaliza un proceso.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
