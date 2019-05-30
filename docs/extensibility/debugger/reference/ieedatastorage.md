---
title: IEEDataStorage | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab42216df5c7d5f3d2d349ccf07e595ab3fc616c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335634"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Esta interfaz representa una matriz de bytes.

## <a name="syntax"></a>Sintaxis

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El evaluador de expresiones (EE) implementa esta interfaz para representar una matriz de bytes (utilizado por los visualizadores de tipo para recuperar y cambiar datos mediante el [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz). EE normalmente implementa esta interfaz para admitir los visualizadores de tipo externo.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Los métodos de la `IPropertyProxyEESide` interfaz todas devuelven esta interfaz. Llame a [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) para obtener el [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaz. Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfaz para obtener el [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 El `IEEDataStorage` interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Recupera el número especificado de bytes de datos a un búfer proporcionado.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Recupera el número de bytes de datos disponibles.|

## <a name="remarks"></a>Comentarios
 Esta interfaz está usando un visualizador de tipo para tener acceso a los datos mantenidos por un objeto específico. Los datos se tratan como una matriz de bytes, lo que permite el visualizador de tipo manipularlos en la forma que se requiere para mostrarla al usuario.

 Un visor personalizado también puede usar esta interfaz, si lo desea, aunque más normalmente, un visor personalizado usa una interfaz personalizada, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (para datos orientados a cadena).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)