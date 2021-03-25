---
description: Esta interfaz implementa métodos clave que proporcionan funcionalidad a las interfaces IDebugProperty3 y IPropertyProxyEESide.
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc712d0c86613d0ee6b30d754b759c17e3ab9bdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086773"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interfaz implementa métodos clave que proporcionan funcionalidad a las interfaces [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .

## <a name="syntax"></a>Sintaxis

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para permitir que un evaluador de expresiones (EE) admita visualizadores de tipos.

## <a name="notes-for-callers"></a>Notas para llamadores
 El EE llama a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) para obtener esta interfaz como parte de su compatibilidad con los visualizadores de tipos.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable

|Método|Descripción|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera el número de visores personalizados sobre los que este servicio sabe.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera la lista de visores personalizados.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Devuelve un objeto proxy para una propiedad.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera el número de cadenas de valor que se van a mostrar para la propiedad o el campo especificados.|

## <a name="remarks"></a>Observaciones
 El IDE usa la interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para determinar si hay visores personalizados o visualizadores de tipo para la propiedad. Al crear un servicio del visualizador (con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), el EE puede proporcionar la funcionalidad a `IDebugProperty3` y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (que permite ver y cambiar el valor de una propiedad) y, por tanto, admite visualizadores de tipos.

 Si un de EE tiene visores personalizados que implementa a su vez, el EE puede anexar los `CLSID` s de esos visores personalizados al final de la lista devuelta por [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Esto permite que EE sea compatible con los visualizadores de tipo y sus propios visores personalizados. Solo tiene que asegurarse de que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) refleje la adición de cualquier visor personalizado.

 Vea [visualizador de tipos y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obtener una explicación de la diferencia entre los visualizadores y los visores.

## <a name="requirements"></a>Requisitos
 Encabezado: EE. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
