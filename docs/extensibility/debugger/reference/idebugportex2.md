---
description: Esta interfaz permite al administrador de depuración de la sesión (SDM) controlar los programas y los procesos que se ejecutan en un puerto.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54da202e6bbaf08216b921afbde2e39f1da3a788
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142796"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Esta interfaz permite al administrador de depuración de la sesión (SDM) controlar los programas y los procesos que se ejecutan en un puerto.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz en el mismo objeto que implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Notas para llamadores
 El SDM llama a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugPort2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugPortEx2` .

|Método|Descripción|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Inicia un archivo ejecutable.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reanuda la ejecución de un proceso.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina si un proceso se puede terminar.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Finaliza un proceso.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtiene el identificador de proceso del propio puerto.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtiene un programa asociado a un nodo de programa.|

## <a name="remarks"></a>Observaciones
 Normalmente, esta interfaz es privada entre el SDM y el proveedor del puerto personalizado.

 Si lo desea, un motor de depuración (DE) puede buscar esta interfaz en la interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) pasada a [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) y usar [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) para iniciar el programa. Sin embargo, esto no es un requisito, y un DE puede hacer todo lo que necesita hacer para iniciar el programa de solicitud.

## <a name="requirements"></a>Requisitos
 Encabezado: portpriv. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
