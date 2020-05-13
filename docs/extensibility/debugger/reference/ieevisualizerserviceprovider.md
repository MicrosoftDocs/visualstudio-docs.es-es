---
title: IEEVisualizerServiceProvider ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717886"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz da acceso a un método que puede crear un servicio de visualizador, que se usa para controlar las tareas del visualizador de tipos para el IDE.

## <a name="syntax"></a>Sintaxis

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para crear un objeto de servicio de visualizador, que a su vez se usa para proporcionar identificadores de clase (`CLSID`s) de visualizadores de tipo para el IDE de Visual Studio.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El evaluador de expresiones (EE) llama a [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable

|Método|Descripción|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea el servicio del visualizador|

## <a name="remarks"></a>Observaciones
 La `IEEVisualizerServiceProvider` interfaz se obtiene durante la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). El servicio de visualizador que crea esta interfaz se usa para proporcionar funcionalidad a una interfaz [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) que el EE es responsable de implementar. El EE también es responsable de implementar una interfaz [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que permite a los visualizadores de tipos ver y modificar el valor de una propiedad.

 Consulte [Visualización y visualización](../../../extensibility/debugger/visualizing-and-viewing-data.md) de datos para obtener más información sobre cómo interactúan estas interfaces.

## <a name="requirements"></a>Requisitos
 Encabezado: ee.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
