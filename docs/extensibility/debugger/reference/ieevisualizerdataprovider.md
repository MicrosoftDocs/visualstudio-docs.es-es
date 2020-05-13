---
title: IEEVisualizerDataProvider ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718054"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz proporciona la capacidad de cambiar el valor de un objeto a través de un visualizador de tipos.

## <a name="syntax"></a>Sintaxis

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones implementa esta interfaz para admitir la modificación de datos en un objeto de propiedad a través de un visualizador de tipos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Esta interfaz se utiliza en la creación de la [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto a través de una llamada a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consulte [Visualización y visualización](../../../extensibility/debugger/visualizing-and-viewing-data.md) de datos para obtener más detalles.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable

|Método|Descripción|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina si es posible actualizar el objeto (y posteriormente, su valor) que representa este visualizador.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Fuerza una reevaluación del objeto para este visualizador.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtiene un objeto existente para este visualizador (no se realiza ninguna evaluación).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Actualiza el objeto para este visualizador, cambiando así el valor que presenta el visualizador.|

## <a name="remarks"></a>Observaciones
 El servicio de visualizador (representado por la interfaz [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) y devuelto por [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene una referencia al objeto que implementa la `IEEVisualizerDataProvider` interfaz. Como resultado, `IEEVisualizerDataProvider` la interfaz no debe implementarse en el mismo objeto que implementa el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si ese objeto mantiene una referencia al `IEEVisualizerService` objeto: se produce una referencia circular y se produce un interbloqueo cuando se destruyen los objetos. El enfoque recomendado `IEEVisualizerDataProvider` es implementar en un `IDebugProperty2` objeto independiente `IUnknown::AddRef` al que el objeto delega sin llamar a él.

## <a name="requirements"></a>Requisitos
 Encabezado: ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
