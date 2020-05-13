---
title: IDebugProgramNodeAttach2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721824"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que un nodo de programa reciba una notificación de un intento de adjuntar al programa asociado.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa en la misma clase que implementa la [interfaz IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para recibir la notificación de una operación de asociación y para proporcionar una oportunidad para cancelar la operación de asociación.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Obtener esta interfaz `QueryInterface` mediante una llamada al método en un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. El [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe llamarse antes de la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para dar al nodo del programa la oportunidad de detener el proceso de conexión.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Se adjunta al programa asociado o aplaza el proceso de conexión al método [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Observaciones
 Esta interfaz es la alternativa preferida al método [de Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) en desuso. Todos los motores de depuración siempre se cargan con la `CoCreateInstance` función, es decir, se crean instancias fuera del espacio de direcciones del programa que se está depurando.

 Si una implementación `IDebugProgramNode2::Attach_V7` anterior del `GUID` método era simplemente establecer el del programa que se está depurando, a continuación, sólo el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método debe implementarse.

 Si una implementación `IDebugProgramNode2::Attach_V7` anterior del método utiliza la interfaz de devolución de llamada que se `IDebugProgramNodeAttach2` proporcionó, esa funcionalidad debe moverse a una implementación de la [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método y la interfaz no tiene que implementarse.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
