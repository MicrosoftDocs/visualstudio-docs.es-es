---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "Interfaz IEEVisualizerDataProvider"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona la capacidad de cambiar el valor de un objeto a través de un visualizador de tipo.  
  
## Sintaxis  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para admitir la modificación de datos en un objeto de propiedad a través de un visualizador de tipo.  
  
## Notas para los llamadores  
 Esta interfaz se utiliza para crear la [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto mediante una llamada a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Vea [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información.  
  
## Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina si es posible actualizar el objeto \(y por consiguiente, su valor\) que representa este visualizador.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Fuerza una reevaluación del objeto para este visualizador.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtiene un objeto existente para este visualizador \(no se realiza ninguna evaluación\).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Actualiza el objeto para este visualizador, con lo que se cambia el valor que se presenta el visualizador.|  
  
## Comentarios  
 El servicio del visualizador \(representado por la [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) de la interfaz y devuelto por [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) mantiene una referencia al objeto que implementa el `IEEVisualizerDataProvider` interfaz. Como resultado, la `IEEVisualizerDataProvider` interfaz no debería implementarse en el mismo objeto que implementa el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si ese objeto mantiene una referencia a la `IEEVisualizerService` objeto: produce una referencia circular y se produce un interbloqueo cuando los objetos se destruyen. El enfoque recomendado es implementar `IEEVisualizerDataProvider` en un objeto independiente para que la `IDebugProperty2` objeto delegados sin llamar a `IUnknown::AddRef` en él.  
  
## Requisitos  
 Encabezado: ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualizar y visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)