---
title: IPropertyProxyProvider | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6d983027a88fd0e116abc7e284eb890eb33261a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124786"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Esta interfaz proporciona una interfaz de proxy para ver y cambiar los datos de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones (EE) implementa esta interfaz en el mismo objeto que implementa el [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz como parte de la compatibilidad de los EE de visualizadores de tipo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProperty3` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 El `IPropertyProxyProvider` interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera una interfaz de proxy de la propiedad para ver los datos en un objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Aunque el EE implementa esta interfaz, la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) normalmente se controla por [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Vea [Visualizing y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información acerca de cómo obtener la interfaz IEEVisualizerService.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizador de tipo y el visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)