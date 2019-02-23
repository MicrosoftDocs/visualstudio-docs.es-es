---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef8fd848ed1a8298cc4ea8a5ce9d2c0463a2b779
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693612"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Esta interfaz permite que la sesión de depuración manager (SDM) notificar a un proceso que está adjuntando a o cuando se desasocia del proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que el [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) con el fin de la interfaz:

- Compatibilidad con seguimiento de las sesiones conectadas a un proceso

- Compatibilidad con la asociación automática a través de varios motores de depuración

  El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.

## <a name="notes-for-callers"></a>Notas para los llamadores

-   Las llamadas SDM [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProcess2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugProcessEx2`.

|Método|Descripción|
|------------|-----------------|
|[Asociar](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa a los procesos que una sesión es ahora el proceso de depuración.|
|[Desasociar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa a los procesos que una sesión ya no está depurando el proceso.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Agrega nodos de programa para obtener una lista de motores de depuración.|

## <a name="remarks"></a>Comentarios
 Esta interfaz es privada entre el SDM y el proceso.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)