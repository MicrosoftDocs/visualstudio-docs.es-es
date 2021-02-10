---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6082b06e6235a93b0e198d973b40efb728bd815
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962137"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Esta interfaz proporciona una interfaz de proxy para ver y cambiar los datos de un objeto.

## <a name="syntax"></a>Sintaxis

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones (EE) implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) como parte de la compatibilidad de EE de los visualizadores de tipos.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProperty3` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 La `IPropertyProxyProvider` interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Recupera una interfaz de proxy de propiedad para ver los datos de un objeto.|

## <a name="remarks"></a>Notas
 Aunque el EE implementa esta interfaz, [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)controla normalmente la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) . Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo obtener la interfaz IEEVisualizerService.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
