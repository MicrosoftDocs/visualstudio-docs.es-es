---
title: IDebugEngineProgram2 ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730300"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Esta interfaz proporciona compatibilidad con depuración multiproceso.

## <a name="syntax"></a>Sintaxis

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor de depuración implementa esta interfaz para admitir la depuración simultánea de varios subprocesos. Esta interfaz se implementa en el mismo objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Utilice [QueryInterface](/cpp/atl/queryinterface) para obtener `IDebugProgram2` esta interfaz de una interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEngineProgram2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Detiene todos los subprocesos que se ejecutan en este programa.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Busca que se produzca la ejecución (o dejar de observar la ejecución) en el subproceso especificado.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite (o no permite) que se produzca la evaluación de expresiones en el subproceso dado, incluso si se detiene el programa.|

## <a name="remarks"></a>Observaciones
 Visual Studio llama a esta interfaz en respuesta a un [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos y para establecer el "Watch for Thread Step" y "Watch for Expression Evaluation on Thread" estados del programa. [Se](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) llama a Stop cada vez que el programa debe ser detenido; este método da al programa la oportunidad de terminar todos los subprocesos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
