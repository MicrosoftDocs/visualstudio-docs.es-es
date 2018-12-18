---
title: Implementación de visualizadores de tipo y visores personalizados | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11d047904e932646eedc974a50590dbe0a9ea99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791285"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementación de visualizadores de tipo y visores personalizados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los visualizadores de tipo y visores personalizados permiten al usuario ver datos de un tipo determinado de forma que sea más significativa que un simple volcado hexadecimal de números. Un evaluador de expresiones (EE) puede asociar los visores personalizados con determinados tipos de datos o variables. Estos visores personalizados se implementan mediante lo EE. EE también admiten los visualizadores de tipo externo, que pueden proceder de otro proveedor de terceros o incluso el usuario final.  
  
## <a name="discussion"></a>Explicación  
  
### <a name="type-visualizers"></a>Visualizadores de tipo  
 Visual Studio solicita una lista de visualizadores de tipo y visores personalizados para todos los objetos que se mostrarán en una ventana Inspección. Un evaluador de expresiones (EE) proporciona una lista de estas características para cada tipo para el que desea admitir visualizadores de tipo y visores personalizados. Las llamadas a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciar todo el proceso de obtener acceso a los visualizadores de tipo y visores personalizados (consulte [visualización y ver datos](../../extensibility/debugger/visualizing-and-viewing-data.md)para obtener más información sobre la secuencia de llamada).  
  
### <a name="custom-viewers"></a>Visores personalizados  
 Visores personalizados se implementan en lo EE para un tipo de datos específico y se representan mediante el [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz. Un visor personalizado no es tan flexible como un visualizador de tipo, porque está disponible solo cuando se está ejecutando el EE que implementa dicho visor personalizado determinado. Implementar un visor personalizado es más sencillo que implementar la compatibilidad de visualizadores de tipo. Sin embargo, que admiten visualizadores de tipo proporciona flexibilidad máxima para el usuario final para visualizar sus datos. El resto de este artículo refiere a solo los visualizadores de tipo.  
  
## <a name="interfaces"></a>Interfaces  
 EE implementa las interfaces siguientes para admitir los visualizadores de tipo, que será consumido por Visual Studio:  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  EE consume las interfaces para admitir los visualizadores de tipo siguientes:  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

