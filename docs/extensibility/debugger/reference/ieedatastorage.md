---
description: Esta interfaz representa una matriz de bytes.
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f24921ec169c458a1b0b5ab1638c1379efd09da1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083367"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Esta interfaz representa una matriz de bytes.

## <a name="syntax"></a>Sintaxis

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones (EE) implementa esta interfaz para representar una matriz de bytes (utilizados por los visualizadores de tipos para recuperar y cambiar los datos a través de la interfaz [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). EE normalmente implementa esta interfaz para admitir visualizadores de tipo externos.

## <a name="notes-for-callers"></a>Notas para llamadores
 Todos los métodos de la `IPropertyProxyEESide` interfaz devuelven esta interfaz. Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener la interfaz [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) para obtener la interfaz [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 La `IEEDataStorage` interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera el número especificado de bytes de datos en un búfer proporcionado.|
|[GetSize (](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera el número de bytes de datos disponibles.|

## <a name="remarks"></a>Observaciones
 Un visualizador de tipos usa esta interfaz para tener acceso a los datos que mantiene un objeto concreto. Los datos se tratan como una matriz de bytes, lo que permite al visualizador de tipos manipularlo de la manera que sea necesario para presentarlo al usuario.

 Un visor personalizado también puede utilizar esta interfaz, si lo desea, aunque más normalmente, un visor personalizado usaría una interfaz personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para los datos orientados a cadenas).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
