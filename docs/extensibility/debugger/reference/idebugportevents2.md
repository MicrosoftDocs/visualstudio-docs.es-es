---
title: IDebugPortEvents2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725173"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Esta interfaz notifica a un agente de escucha (normalmente el administrador de depuración de sesión [SDM] o un motor de depuración) de la creación y destrucción de procesos y programas en un puerto determinado. Esta información se puede utilizar para presentar una vista en tiempo real de los procesos y programas que se ejecutan en el puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio normalmente implementa esta interfaz para recibir notificaciones sobre la creación y destrucción del programa. Un motor de depuración también puede implementar esta interfaz para escuchar dichos eventos de puerto.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Todas las interfaces [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) se <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> pueden consultar para una interfaz. A <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> continuación, `IDebugPortEvents2` se llama <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> al método <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> para en la interfaz para obtener una interfaz. Por último, se llama al <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método de la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz para enviar los eventos a través del método [Event.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugPortEvents2`se muestra el método de .

|Método|Descripción|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envía eventos que describen la creación y destrucción de procesos y programas en el puerto.|

## <a name="remarks"></a>Observaciones
 `IDebugPortEvents2`También es utilizado por el SDM para depurar los programas que se ejecutan en un proceso que ya se está depurando.

 Los eventos de puerto se pasan al SDM por esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
