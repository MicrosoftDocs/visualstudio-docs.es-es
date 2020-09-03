---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730300"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Esta interfaz proporciona compatibilidad con la depuración multiproceso.

## <a name="syntax"></a>Sintaxis

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor de depuración implementa esta interfaz para admitir la depuración simultánea de varios subprocesos. Esta interfaz se implementa en el mismo objeto que implementa la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de una `IDebugProgram2` interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEngineProgram2` .

|Método|Descripción|
|------------|-----------------|
|[Detención](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Detiene todos los subprocesos que se ejecutan en este programa.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Inspecciona la ejecución (o deja de ver la ejecución) para que se produzca en el subproceso determinado.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite (o no) que se produzca la evaluación de expresiones en el subproceso determinado, incluso si el programa está detenido.|

## <a name="remarks"></a>Observaciones
 Visual Studio llama a esta interfaz como respuesta a un evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y establece los Estados "inspeccionar paso de subproceso" y "inspeccionar para evaluación de expresiones en el subproceso" del programa. Se llama a [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) cuando el programa se va a detener; Este método proporciona al programa una oportunidad para finalizar todos los subprocesos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
