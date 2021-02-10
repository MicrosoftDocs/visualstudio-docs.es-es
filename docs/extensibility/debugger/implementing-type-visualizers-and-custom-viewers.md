---
title: Implementar visualizadores de tipos y visores personalizados | Microsoft Docs
description: Obtenga información sobre cómo implementar visualizadores de tipos y visores personalizados, que permiten a los usuarios ver los datos de una manera más significativa que un volcado de números.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8cf456dca27a45a2674f7138a6c0b21b12750c81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945973"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Implementar visualizadores de tipos y visores personalizados
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Los visualizadores de tipos y los visores personalizados permiten a un usuario ver los datos de un tipo determinado de una manera más significativa que un volcado hexadecimal sencillo de números. Un evaluador de expresiones (EE) puede asociar visores personalizados a tipos específicos de datos o variables. Estos visores personalizados se implementan en EE. EE también admite visualizadores de tipos externos, que pueden provienen de otro proveedor de terceros o incluso del usuario final.

## <a name="discussion"></a>Debate

### <a name="type-visualizers"></a>Visualizadores de tipos
 Visual Studio solicita una lista de visualizadores de tipo y visores personalizados para cada objeto que se va a mostrar en una ventana Inspección. Un evaluador de expresiones (EE) proporciona una lista de este tipo para todos los tipos para los que desea admitir visualizadores de tipos y visores personalizados. Las llamadas a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) inician todo el proceso de acceso a los visualizadores de tipo y a los visores personalizados (vea [visualizar y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener detalles sobre la secuencia de llamada).

### <a name="custom-viewers"></a>Visores personalizados
 Los visores personalizados se implementan en EE para un tipo de datos específico y se representan mediante la interfaz [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) . Un visor personalizado no es tan flexible como un visualizador de tipos, ya que solo está disponible cuando es el de EE que implementa que se está ejecutando un visor personalizado determinado. Implementar un visor personalizado es más sencillo que implementar la compatibilidad con los visualizadores de tipos. Sin embargo, los visualizadores de tipos auxiliares proporcionan la máxima flexibilidad al usuario final para visualizar sus datos. El resto de este debate solo se refiere a los visualizadores de tipos.

## <a name="interfaces"></a>Interfaces
 El EE implementa las siguientes interfaces para admitir los visualizadores de tipos que se van a usar en Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE usa las siguientes interfaces para admitir los visualizadores de tipos:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizar y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
