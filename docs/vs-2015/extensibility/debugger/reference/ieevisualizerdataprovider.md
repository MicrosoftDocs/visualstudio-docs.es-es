---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86ad3f3ecec94c4c0773325ed2a571171b1f9b33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843254"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona la capacidad de cambiar el valor de un objeto a través de un visualizador de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones implementa esta interfaz para admitir la modificación de datos en un objeto de propiedad a través de un visualizador de tipos.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Esta interfaz se usa para crear el objeto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) a través de una llamada a [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más detalles.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Determina si es posible actualizar el objeto (y, posteriormente, su valor) que representa este visualizador.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Fuerza una nueva evaluación del objeto para este visualizador.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtiene un objeto existente para este visualizador (no se realiza ninguna evaluación).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Actualiza el objeto para este visualizador, con lo que se cambia el valor que presenta el visualizador.|  
  
## <a name="remarks"></a>Notas  
 El servicio visualizador (tal como se representa mediante la interfaz [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) y devuelto por [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) mantiene una referencia al objeto que implementa la `IEEVisualizerDataProvider` interfaz. Como resultado, la `IEEVisualizerDataProvider` interfaz no debe implementarse en el mismo objeto que implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) si ese objeto mantiene una referencia al `IEEVisualizerService` objeto: se producen una referencia circular y se produce un interbloqueo cuando se destruyen los objetos. El enfoque recomendado consiste en implementar `IEEVisualizerDataProvider` en un objeto independiente al que el `IDebugProperty2` objeto delegue sin llamar a `IUnknown::AddRef` en él.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: EE. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
