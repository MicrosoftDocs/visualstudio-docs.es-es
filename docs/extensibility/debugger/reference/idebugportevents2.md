---
title: IDebugPortEvents2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725173"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Esta interfaz notifica a un agente de escucha (normalmente, el administrador de depuración de sesión [SDM] o un motor de depuración) de la creación y destrucción de procesos y programas en un puerto determinado. Esta información se puede usar para presentar una vista en tiempo real de los procesos y programas que se ejecutan en el puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Normalmente, Visual Studio implementa esta interfaz para recibir notificaciones sobre la creación y destrucción de programas. Un motor de depuración también puede implementar esta interfaz para escuchar estos eventos de puerto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Todas las interfaces [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) se pueden consultar para una <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz. A continuación, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> se llama al método para `IDebugPortEvents2` en la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz para obtener una <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz. Por último, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> se llama al método en la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz para enviar los eventos a través del método de [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestra el método de `IDebugPortEvents2` .

|Método|Descripción|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envía eventos que describen la creación y destrucción de procesos y programas en el puerto.|

## <a name="remarks"></a>Observaciones
 `IDebugPortEvents2` el SDM también lo usa para depurar programas que se ejecutan en un proceso que ya se está depurando.

 Esta interfaz pasa los eventos de puerto al SDM.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
