---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33f1d88eaa7fe6cce34f4b386998ecc68cfe4953
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934484"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Esta interfaz proporciona compatibilidad con la depuración multiproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir la depuración simultánea de varios subprocesos. Esta interfaz se implementa en el mismo objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde un `IDebugProgram2` interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEngineProgram2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Detiene todos los subprocesos que se ejecutan en este programa.|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Supervisa la ejecución (o Detener ejecución inspeccionando) que se produzca en el subproceso especificado.|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permite la evaluación de expresiones que se produzca en el subproceso determinado, incluso si se detiene el programa (o impide).|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio llama a esta interfaz en respuesta a una [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos y establecer los Estados "Watch para subprocesos paso" y "Watch para expresión de evaluación en el subproceso" del programa. [Detener](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) se llama cada vez que el programa se detenga; este método da al programa la oportunidad de finalizar todos los subprocesos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)