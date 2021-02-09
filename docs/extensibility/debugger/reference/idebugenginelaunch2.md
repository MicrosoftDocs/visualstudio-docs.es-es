---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4485001341399d3830864a30b64fec24a77c5a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892728"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Lo usa un motor DE depuración (DE) para iniciar y finalizar programas.

## <a name="syntax"></a>Sintaxis

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un personalizado DE si tiene requisitos especiales para iniciar un proceso que no se puede controlar por completo mediante un puerto personalizado. Suele ser el caso cuando el DE forma parte de un intérprete y el proceso que se está depurando es un script: el intérprete debe iniciarse primero y, a continuación, el script se carga y se inicia. Un puerto puede iniciar el intérprete, pero el script puede requerir un tratamiento especial (que es donde el DE tiene un rol). Esta interfaz solo se implementa si hay requisitos únicos para iniciar un programa que un puerto personalizado no puede controlar.

## <a name="notes-for-callers"></a>Notas para llamadores
 El administrador de depuración de sesión (SDM) llama a esta interfaz si el SDM puede obtener esta interfaz de la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (mediante QueryInterface). Si se puede obtener esta interfaz, el SDM sabe que el DE tiene requisitos especiales y llama a esta interfaz para iniciar el programa en lugar de hacer que el puerto lo inicie.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEngineLaunch2` .

|Método|Descripción|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia un proceso por medio de la de.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reanuda la ejecución del proceso.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina si se puede finalizar un proceso.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Finaliza un proceso.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
