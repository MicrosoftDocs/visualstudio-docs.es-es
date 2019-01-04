---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a738ecb042fa423cf165a42a9d472e06f23648d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887190"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Esta interfaz representa los bytes de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar los bytes de memoria.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) devuelve esta interfaz para proporcionar acceso a la memoria del sistema. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) y [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) devolver esta interfaz para proporcionar acceso a los bytes de un objeto.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugMemoryBytes2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lee una secuencia de bytes, empezando en una ubicación determinada.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Escribe `dwCount` bytes, empezando en `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtiene el tamaño, en bytes, de la memoria representado por esta interfaz.|  
  
## <a name="remarks"></a>Comentarios  
 Para las propiedades, un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa una matriz proporciona un `IDebugMemoryBytes2` interfaz para tener acceso a los valores de la matriz.  
  
 Visual Studio **vista memoria** llamadas [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) para recuperar un `IDebugMemoryBytes2` interfaz para tener acceso a memoria del sistema. Se obtiene la dirección para tener acceso mediante el análisis de la expresión escrita como una dirección en la vista de la memoria y, a continuación, evaluar la expresión analizada utilizando [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener un `IDebugProperty2` interfaz. Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) devuelve el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que describe la dirección de memoria. Este contexto de la memoria, a continuación, se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)