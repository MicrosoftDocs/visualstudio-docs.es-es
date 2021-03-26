---
description: Esta interfaz proporciona una interfaz de proxy para ver y cambiar los datos de un objeto.
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87bc0bfa11c54f8eade595f6bf0bfaba1fa277ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058097"
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

## <a name="remarks"></a>Observaciones
 Aunque el EE implementa esta interfaz, [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)controla normalmente la implementación de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) . Vea [visualizar y ver datos](../../../extensibility/debugger/visualizing-and-viewing-data.md) para obtener más información sobre cómo obtener la interfaz IEEVisualizerService.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Visualización de datos](../../../extensibility/debugger/visualizing-and-viewing-data.md)
