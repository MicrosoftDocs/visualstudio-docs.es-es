---
description: Esta interfaz proporciona acceso a un método que puede crear un servicio del visualizador, que se utiliza para controlar las tareas del visualizador de tipos para el IDE.
title: IEEVisualizerServiceProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d4fc53ae13588a0e285e4a62691da4d88a94d5f5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227182"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz proporciona acceso a un método que puede crear un servicio del visualizador, que se utiliza para controlar las tareas del visualizador de tipos para el IDE.

## <a name="syntax"></a>Sintaxis

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para crear un objeto de servicio del visualizador, que a su vez se usa para proporcionar `CLSID` los identificadores de clase de los visualizadores de tipo al IDE de Visual Studio.

## <a name="notes-for-callers"></a>Notas para llamadores
 El evaluador de expresiones (EE) llama a [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable

|Método|Descripción|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea el servicio del visualizador.|

## <a name="remarks"></a>Observaciones
 La `IEEVisualizerServiceProvider` interfaz se obtiene durante la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). El servicio visualizador que crea esta interfaz se usa para proporcionar funcionalidad a una interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , que es responsable de la implementación de EE. EE también es responsable de implementar una interfaz [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) que permita a los visualizadores de tipos ver y modificar el valor de una propiedad.

 Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo interactúan estas interfaces.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
