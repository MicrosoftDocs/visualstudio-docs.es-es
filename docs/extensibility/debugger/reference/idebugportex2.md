---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bed6cd047af4ba57a1880d87e30a990dcf83efac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340428"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Esta interfaz permite que la sesión de depuración control manager (SDM), los programas y procesos que se ejecutan en un puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Notas para los llamadores
 Las llamadas SDM [QueryInterface](/cpp/atl/queryinterface) en el `IDebugPort2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugPortEx2`.

|Método|Descripción|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Inicia un archivo ejecutable.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reanuda la ejecución de un proceso.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina si se puede terminar un proceso.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina un proceso.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtiene el identificador de proceso del puerto de sí mismo.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtiene un programa asociado con un nodo de programa.|

## <a name="remarks"></a>Comentarios
 Esta interfaz es normalmente privada entre el SDM y el proveedor de puerto personalizado.

 Si lo desea, puede buscar un motor de depuración (DE) para esta interfaz el [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz pasa a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) y usar [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) para iniciar el programa. Sin embargo, esto es no es un requisito, y a DE puede hacer todo lo que debe hacer para iniciar el programa de la solicitud.

## <a name="requirements"></a>Requisitos
 Encabezado: portpriv.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)