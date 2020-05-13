---
title: IDebugObject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726315"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa un objeto que crea el enlazador para encapsular los valores de símbolos y expresiones.

## <a name="syntax"></a>Sintaxis

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador de expresiones implementa esta interfaz para representar un objeto.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz es la clase base para todos los objetos que utiliza el evaluador de expresiones en expresiones analizadas. Se devuelve mediante una llamada a la [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) método. [QueryInterface](/cpp/atl/queryinterface) obtiene las interfaces más especializadas de esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugObject`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtiene el tamaño del objeto.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtiene el valor del objeto como una serie consecutiva de bytes.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Establece el valor del objeto a partir de una serie consecutiva de bytes.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Establece el valor de referencia de este objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtiene el contexto de memoria que representa la dirección del valor del objeto.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Comprueba si este objeto es una referencia nula.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara un objeto con éste.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina si este objeto es de solo lectura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina si el objeto es un proxy transparente.|

## <a name="remarks"></a>Observaciones
 El evaluador de expresiones utiliza esta interfaz como clase base para representar objetos en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)
