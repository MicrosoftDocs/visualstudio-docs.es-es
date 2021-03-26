---
description: Esta interfaz permite al administrador de depuración de la sesión (SDM) notificar a un proceso que está adjuntando o desasociando del proceso.
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bd22a779cd0a474b5df03d2315402dbe1a25239
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081521"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Esta interfaz permite al administrador de depuración de la sesión (SDM) notificar a un proceso que está adjuntando o desasociando del proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz en el mismo objeto que la interfaz [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para:

- Compatibilidad con el seguimiento de sesiones conectadas a un proceso

- Compatibilidad con la Asociación automática entre varios motores de depuración

  El proveedor del puerto personalizado puede implementar esta interfaz si elige.

## <a name="notes-for-callers"></a>Notas para llamadores

- El SDM llama a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProcess2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProcessEx2` .

|Método|Descripción|
|------------|-----------------|
|[Adjuntar](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa al proceso de que una sesión está depurando el proceso.|
|[Separar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa al proceso de que una sesión ya no está depurando el proceso.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Agrega nodos de programa para una lista de motores de depuración.|

## <a name="remarks"></a>Observaciones
 Esta interfaz es privada entre el SDM y el proceso.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
