---
title: "Implementaci&#243;n de tipo visualizadores y visores personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], de visor personalizado"
  - "depurar [SDK de depuración], Visualizador de tipo"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementaci&#243;n de tipo visualizadores y visores personalizados
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los visualizadores de tipo y visores personalizados permiten al usuario ver los datos de un tipo determinado de forma que sea más significativa que un volcado hexadecimal simple de números. Un evaluador de expresiones \(EE\) puede asociar los visores personalizados con determinados tipos de datos o variables. Estos visores personalizados se implementan mediante lo EE. EE también admiten los visualizadores de tipo externo, pueden proceder de otro proveedor de terceros o incluso el usuario final.  
  
## Explicación  
  
### Visualizadores de tipo  
 Visual Studio solicita una lista de visualizadores de tipo y visores personalizados para todos los objetos que se mostrará en una ventana de inspección. Un evaluador de expresiones \(EE\) proporciona esta lista para cada tipo para el que desea admitir los visualizadores de tipo y visores personalizados. Las llamadas a [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) y [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciar todo el proceso de obtener acceso a los visualizadores de tipo y visores personalizados \(consulte [Visualizar y visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre la secuencia de llamada\).  
  
### Visores personalizados  
 Visores personalizados se implementan en lo EE para un tipo de datos específico y se representan mediante la [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaz. Un visor personalizado no es tan flexible como un visualizador de tipo, ya que está disponible sólo cuando se está ejecutando el EE que implementa dicho visor personalizado determinado. Implementar un visor personalizado es más sencillo que implementar la compatibilidad de los visualizadores de tipo. Sin embargo, compatible con los visualizadores de tipo proporciona máxima flexibilidad para el usuario final para visualizar sus datos. El resto de este artículo se refiere a sólo los visualizadores de tipo.  
  
## Interfaces  
 EE implementa las interfaces siguientes para admitir los visualizadores de tipo, para ser consumido por Visual Studio:  
  
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
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizar y visualización de datos](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)