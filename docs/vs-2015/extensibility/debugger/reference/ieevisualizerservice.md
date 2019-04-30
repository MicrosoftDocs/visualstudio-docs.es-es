---
title: IEEVisualizerService | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3bb741aa25cf6695f1dd1d8d66fc0c1846413b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435513"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz implementa métodos clave que proporcionan funcionalidades para el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaces.  
  
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
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Recupera el número de visores personalizados sobre qué sabe este servicio.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Recupera la lista de visores personalizados.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Devuelve un objeto proxy para una propiedad.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Recupera el número de cadenas de valor que se muestra en la propiedad especificada o el campo.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE usa la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para determinar si existen todos los visores personalizados o escriba visualizadores para la propiedad. Mediante la creación de un servicio visualizador (con [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), el EE puede proporcionar la funcionalidad para el `IDebugProperty3` y [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (que permite ver y cambiar una valor de la propiedad), por tanto, admiten visualizadores de tipo e interfaces.  
  
 Si un EE tiene visores personalizados que implementa, puede anexar el EE el `CLSID`s de los visores personalizados para el final de la lista devuelta por [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Esto permite un EE admitir los visualizadores de tipo y sus propios visores personalizados. Simplemente asegúrese de que [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) refleja la suma de todos los visores personalizados.  
  
 Consulte [visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) para obtener una explicación de la diferencia entre los visualizadores y visores.  
  
## <a name="requirements"></a>Requisitos  
 Header: ee.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
