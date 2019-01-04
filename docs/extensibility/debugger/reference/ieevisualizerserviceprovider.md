---
title: IEEVisualizerServiceProvider | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed17748a2c635de5b4a4b715d4061ee3841f18ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990443"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona acceso a un método que puede crear un servicio del visualizador, que se utiliza para controlar las tareas del visualizador de tipo para el IDE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz para crear un objeto de servicio del visualizador, que a su vez se usa para proporcionar el Id. de clase (`CLSID`s) de visualizadores de tipo para el IDE de Visual Studio.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El evaluador de expresiones (EE) llama a [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crea el servicio del visualizador|  
  
## <a name="remarks"></a>Comentarios  
 El `IEEVisualizerServiceProvider` interfaz se obtiene durante la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). El servicio del visualizador que crea esta interfaz se usa para proporcionar funcionalidad a un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz, que es responsable de implementar lo EE. También es responsable de implementar el EE un [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaz que permite a los visualizadores de tipo ver y modificar el valor de la propiedad.  
  
 Consulte [visualización y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo interactúan estas interfaces.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)