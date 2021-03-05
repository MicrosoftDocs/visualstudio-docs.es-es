---
description: Permite que un nodo de programa reciba una notificación de un intento de asociarse al programa asociado.
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa623097224afc4f3a6b93d6b98ece0e14149ca5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171739"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que un nodo de programa reciba una notificación de un intento de asociarse al programa asociado.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa en la misma clase que implementa la interfaz [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para recibir la notificación de una operación de adjuntar y proporcionar una oportunidad para cancelar la operación de adjuntar.

## <a name="notes-for-callers"></a>Notas para llamadores
 Obtenga esta interfaz llamando al `QueryInterface` método en un objeto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Se debe llamar al método [AutoAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) antes del método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) para dar al nodo del programa una oportunidad de detener el proceso de asociación.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Se adjunta al programa asociado o pospone el proceso de asociación al método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Observaciones
 Esta interfaz es la alternativa preferida al método [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) obsoleto. Todos los motores de depuración siempre se cargan con la `CoCreateInstance` función, es decir, se crean instancias fuera del espacio de direcciones del programa que se está depurando.

 Si una implementación anterior del `IDebugProgramNode2::Attach_V7` método simplemente estaba estableciendo el `GUID` del programa que se está depurando, solo es necesario implementar el método [AutoAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Si una implementación anterior del `IDebugProgramNode2::Attach_V7` método usaba la interfaz de devolución de llamada que se proporcionó, esa funcionalidad debe moverse a una implementación del método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) y no es `IDebugProgramNodeAttach2` necesario implementar la interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
