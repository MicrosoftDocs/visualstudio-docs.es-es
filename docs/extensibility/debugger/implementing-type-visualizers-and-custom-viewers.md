---
title: Implementar los visualizadores de tipo y visores personalizados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c56d093c2e6380b29c8c9a788ea34d148fbe64b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementar los visualizadores de tipo y visores personalizados
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los visualizadores de tipo y visores personalizados permiten a un usuario ver datos de un tipo determinado de forma que sea más significativa que un volcado hexadecimal simple de números. Un evaluador de expresiones (EE) puede asociar los visores personalizados con determinados tipos de datos o variables. Estos visores personalizados se implementan mediante lo EE. El EE también admite los visualizadores de tipo externo, lo que podrían proceder de otro proveedor de terceros o incluso el usuario final.  
  
## <a name="discussion"></a>Explicación  
  
### <a name="type-visualizers"></a>Visualizadores de tipo  
 Visual Studio le pide una lista de visualizadores de tipo y los visores personalizados para todos los objetos que se mostrarán en una ventana Inspección. Un evaluador de expresiones (EE) proporciona una lista de este tipo para cada tipo para el que desea admitir los visualizadores de tipo y visores personalizados. Las llamadas a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciar todo el proceso de acceso a los visualizadores de tipo y los visores personalizados (consulte [Visualizing y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md)para obtener más información sobre la secuencia de llamada).  
  
### <a name="custom-viewers"></a>Visores personalizados  
 Visores personalizados se implementan en lo EE para un tipo de datos específico y se representan mediante la [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz. Un visor personalizado no es tan flexible como un visualizador de tipo, ya que está disponible solo cuando se está ejecutando el EE que implementa ese visor personalizado determinado. Implementar un visor personalizado es más sencillo que implementar la compatibilidad de los visualizadores de tipo. Sin embargo, admiten los visualizadores de tipo proporciona una flexibilidad máxima para el usuario final para visualizar sus datos. El resto de este tema se refiere a solo los visualizadores de tipo.  
  
## <a name="interfaces"></a>Interfaces  
 El EE implementa las interfaces siguientes para admitir los visualizadores de tipo, que será consumido por Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE consume las interfaces para admitir los visualizadores de tipo siguientes:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizar y visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)