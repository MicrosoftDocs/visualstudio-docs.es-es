---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 660c792d9e13fabbd433aee46c57474fb824453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684673"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona métodos para ver los datos en el objeto asociado. Esta interfaz forma parte de la compatibilidad con los visualizadores de tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un evaluador de expresiones implementa esta interfaz para admitir los visualizadores de tipos.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener esta interfaz. Llame a [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en una interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obtener la interfaz [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden vtable  
 Esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa un proveedor de origen de datos para que se pueda tener acceso a los datos del objeto.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera información acerca del ensamblado del objeto.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtiene los datos iniciales del objeto.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia de un almacenamiento de datos existente.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea una referencia a un almacenamiento de datos existente.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera información sobre un ensamblado específico en el contexto del ensamblado que contiene este objeto.|  
  
## <a name="remarks"></a>Observaciones  
 Un visualizador de tipos usa esta interfaz para tener acceso a los valores asociados al objeto del que forma parte esta interfaz. Se obtiene acceso a los datos a través de la interfaz [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , que proporciona una vista de solo lectura de los datos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualizador de tipos y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
