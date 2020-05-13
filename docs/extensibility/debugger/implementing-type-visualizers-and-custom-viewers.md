---
title: Implementación de visualizadores de tipos y visores personalizados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738508"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementar visualizadores de tipos y visores personalizados
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Los visualizadores de tipos y los visores personalizados permiten a un usuario ver datos de un tipo determinado de una manera más significativa que un simple volcado hexadecimal de números. Un evaluador de expresiones (EE) puede asociar visores personalizados con tipos específicos de datos o variables. Estos visores personalizados son implementados por EE. El EE también puede admitir visualizadores de tipo externo, que podrían provenir de otro proveedor externo o incluso del usuario final.

## <a name="discussion"></a>Discusión

### <a name="type-visualizers"></a>Visualizadores de tipo
 Visual Studio solicita una lista de visualizadores de tipos y visores personalizados para cada objeto que se mostrará en una ventana de inspección. Un evaluador de expresiones (EE) proporciona dicha lista para cada tipo para el que desea admitir visualizadores de tipos y visores personalizados. Las llamadas a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) inician todo el proceso de acceso a visualizadores de tipos y visores personalizados (consulte [Visualización y visualización](../../extensibility/debugger/visualizing-and-viewing-data.md) de datos para obtener más información sobre la secuencia de llamada).

### <a name="custom-viewers"></a>Visores personalizados
 Los visores personalizados se implementan en el EE para un tipo de datos específico y se representan mediante el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz. Un visor personalizado no es tan flexible como un visualizador de tipos, ya que solo está disponible cuando se ejecuta el EE que implementa ese visor personalizado determinado. Implementar un visor personalizado es más sencillo que implementar la compatibilidad con visualizadores de tipos. Sin embargo, la compatibilidad con visualizadores de tipos proporciona la máxima flexibilidad al usuario final para visualizar sus datos. El resto de esta discusión se refiere únicamente a los visualizadores de tipos.

## <a name="interfaces"></a>Interfaces
 EE implementa las siguientes interfaces para admitir visualizadores de tipos, que visualde Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE consume las siguientes interfaces para admitir visualizadores de tipos:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualización y visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
