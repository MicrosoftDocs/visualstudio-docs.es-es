---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700043"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona una interfaz de proxy para ver y cambiar los datos de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones (EE) implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) como parte de la compatibilidad de EE de los visualizadores de tipos.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Llame a [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en una `IDebugProperty3` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden vtable  
 La `IPropertyProxyProvider` interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera una interfaz de proxy de propiedad para ver los datos de un objeto.|  
  
## <a name="remarks"></a>Observaciones  
 Aunque el EE implementa esta interfaz, [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)controla normalmente la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) . Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo obtener la interfaz IEEVisualizerService.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualizador de tipos y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
