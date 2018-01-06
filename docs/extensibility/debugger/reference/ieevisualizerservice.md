---
title: IEEVisualizerService | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService
helpviewer_keywords: IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97701dede6a3e6b17911f6ab3c5e37dfdd90cc58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz implementa métodos clave que proporcionan funcionalidades para la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaces.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz para permitir que un evaluador de expresiones (EE) para admitir los visualizadores de tipo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Las llamadas EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) para obtener esta interfaz como parte de su compatibilidad con los visualizadores de tipo.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera el número de visores personalizados sobre los cuales se conoce este servicio.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera la lista de visores personalizados.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Devuelve un objeto de proxy para una propiedad.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera el número de cadenas de valor para mostrar de la propiedad especificada o el campo.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE usa la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para determinar si existen los visores personalizados o escriba visualizadores para la propiedad. Mediante la creación de un servicio del visualizador (con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), el EE puede proporcionar la funcionalidad para la `IDebugProperty3` y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (que admite ver y cambiar una valor de la propiedad) e interfaces, con lo que se admiten los visualizadores de tipo.  
  
 Si un EE tiene visores personalizados que implementa, puede anexar el EE el `CLSID`s de los visores personalizados al final de la lista devuelta por [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Esto permite un EE admitir los visualizadores de tipo y sus propios visores personalizados. Simplemente asegúrese de que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) refleja la adición de los visores personalizados.  
  
 Vea [visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obtener una descripción de la diferencia entre los visualizadores y visores.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)