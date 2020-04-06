---
title: IPropertyProxyEESide (IPropertyProxyEESide) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714857"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Esta interfaz proporciona métodos para ver los datos del objeto asociado. Esta interfaz forma parte de la compatibilidad con visualizadores de tipos.

## <a name="syntax"></a>Sintaxis

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un evaluador de expresiones implementa esta interfaz para admitir visualizadores de tipos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener esta interfaz. Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para obtener el [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicializa un proveedor de origen de datos para que se pueda tener acceso a los datos del objeto.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Recupera información sobre el ensamblado del objeto.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Obtiene los datos iniciales del objeto.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Crea una copia de un almacenamiento de datos existente.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Crea una referencia a un almacenamiento de datos existente.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Recupera información sobre un ensamblado específico en el contexto del ensamblado que contiene este objeto.|

## <a name="remarks"></a>Observaciones
 Un visualizador de tipos utiliza esta interfaz para tener acceso a los valores asociados con el objeto del que forma parte esta interfaz. Se tiene acceso a los datos a través de la interfaz [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) que proporciona una vista de solo lectura de los datos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
