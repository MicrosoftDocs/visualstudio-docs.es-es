---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd9b804556cd748c921a0c21729daee56e9499b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708464"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Esta interfaz proporciona métodos para ver los datos en el objeto asociado. Esta interfaz es parte de la compatibilidad con los visualizadores de tipo.

## <a name="syntax"></a>Sintaxis

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador implementa esta interfaz para admitir los visualizadores de tipo.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener esta interfaz. Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para obtener el [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa un proveedor de origen de datos para que se pueden tener acceso a los datos del objeto.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera información sobre el ensamblado del objeto.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtiene los datos iniciales para el objeto.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia de un almacenamiento de datos existente.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea una referencia a un almacenamiento de datos existente.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera información sobre un ensamblado concreto en el contexto del ensamblado que contiene este objeto.|

## <a name="remarks"></a>Comentarios
 Un visualizador de tipo usa esta interfaz para tener acceso a los valores asociados con el objeto que forma parte de esta interfaz. Se tiene acceso a los datos a través de la [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfaz, que proporciona una vista de solo lectura de los datos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)