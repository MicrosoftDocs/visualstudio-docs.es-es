---
title: IEEDataStorage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aeb98c4c4d3b544616412b3cf5cf8a162fddbd6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120834"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Esta interfaz representa una matriz de bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador de expresiones (EE) implementa esta interfaz para representar una matriz de bytes (utilizando los visualizadores de tipo para recuperar y modificar datos a través de la [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz). Normalmente, el EE implementa esta interfaz para admitir los visualizadores de tipo externo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Los métodos de la `IPropertyProxyEESide` interfaz todos devolver esta interfaz. Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener la [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz. Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para obtener el [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 El `IEEDataStorage` interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera el número especificado de bytes de datos a un búfer proporcionado.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera el número de bytes de datos disponibles.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa con un visualizador de tipo para tener acceso a los datos mantenidos por un objeto específico. Los datos se tratan como una matriz de bytes, lo que permite el visualizador de tipo manipular en la forma que se requiere para presentar al usuario.  
  
 Un visor personalizado también puede utilizar esta interfaz, si lo desea, aunque por lo general, un visor personalizado podría usar una interfaz personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para datos en forma de cadena).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)