---
title: IPropertyProxyProvider ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714797"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Esta interfaz proporciona una interfaz proxy para ver y cambiar los datos de un objeto.

## <a name="syntax"></a>Sintaxis

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones (EE) implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) como parte de la compatibilidad del EE de visualizadores de tipos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProperty3` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 La `IPropertyProxyProvider` interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera una interfaz de proxy de propiedad para ver los datos de un objeto.|

## <a name="remarks"></a>Observaciones
 Aunque el EE implementa esta interfaz, la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) normalmente se controla mediante [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Consulte [Visualización y visualización](../../../extensibility/debugger/visualizing-and-viewing-data.md) de datos para obtener más información sobre cómo obtener la interfaz IEEVisualizerService.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
