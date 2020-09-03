---
title: IDebugObject | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726315"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz representa un objeto que el enlazador crea para encapsular los valores de símbolos y expresiones.

## <a name="syntax"></a>Sintaxis

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador de expresiones implementa esta interfaz para representar un objeto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz es la clase base para todos los objetos que el evaluador de expresiones utiliza en expresiones analizadas. Se devuelve mediante una llamada al método [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) . [QueryInterface](/cpp/atl/queryinterface) obtiene las interfaces más especializadas de esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugObject` .

|Método|Descripción|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Obtiene el tamaño del objeto.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Obtiene el valor del objeto como una serie consecutiva de bytes.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Establece el valor del objeto a partir de una serie consecutiva de bytes.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Establece el valor de referencia de este objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Obtiene el contexto de memoria que representa la dirección del valor del objeto.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Comprueba si este objeto es una referencia nula.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Compara un objeto con este.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Determina si este objeto es de solo lectura.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Determina si el objeto es un proxy transparente.|

## <a name="remarks"></a>Observaciones
 El evaluador de expresiones utiliza esta interfaz como la clase base para representar objetos en un árbol de análisis.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Volver](../../../extensibility/debugger/reference/idebugbinder-bind.md)
