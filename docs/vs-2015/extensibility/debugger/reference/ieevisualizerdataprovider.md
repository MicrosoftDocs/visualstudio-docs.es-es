---
title: IEEVisualizerDataProvider | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 844f591055eb309be3ff14171d937b2998d47c71
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724091"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona la capacidad de cambiar el valor de un objeto a través de un visualizador de tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para admitir la modificación de los datos en un objeto de propiedad a través de un visualizador de tipo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se utiliza para crear el [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto mediante una llamada a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Consulte [visualización y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más detalles.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina si es posible actualizar el objeto (y por consiguiente, su valor) que representa este visualizador.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Fuerza una nueva evaluación del objeto para este visualizador.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtiene un objeto existente para este visualizador (no se realiza ninguna evaluación).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Actualiza el objeto para este visualizador, con lo que se cambia el valor que se presenta el visualizador.|  
  
## <a name="remarks"></a>Comentarios  
 El servicio del visualizador (tal como está representada por la [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfaz y devuelto por [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene una referencia al objeto que implementa el `IEEVisualizerDataProvider` interfaz . Como resultado, el `IEEVisualizerDataProvider` interfaz no debe implementarse en el mismo objeto que implementa el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si ese objeto mantiene una referencia a la `IEEVisualizerService` objeto: resultados de una referencia circular y un interbloqueo se produce cuando los objetos se destruyen. El enfoque recomendado consiste en implementar `IEEVisualizerDataProvider` en un objeto independiente para que el `IDebugProperty2` objeto delegados sin llamar a `IUnknown::AddRef` en él.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)

