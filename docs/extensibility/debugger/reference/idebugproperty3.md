---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f24e7ec1842866011bb4d3735104a043bc77e01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897263"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Esta interfaz proporciona compatibilidad con:

- Recuperar una cadena arbitrariamente larga asociada a la propiedad.

- Asociar un identificador único a la propiedad.

- Recuperar una lista de visores personalizados para la propiedad.

- Establecer el valor de una propiedad con la capacidad de notificar los errores resultantes

## <a name="syntax"></a>Sintaxis

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz en el mismo objeto que implementa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para proporcionar compatibilidad con cadenas largas, identificadores de propiedad y visores personalizados.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProperty2` interfaz para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos heredados de `IDebugProperty2` , la `IDebugProperty3` interfaz expone los métodos siguientes.

|Método|Descripción|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Devuelve la longitud de la cadena asociada a la propiedad.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Devuelve la cadena en un búfer proporcionado por el usuario.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crea un identificador único para esta propiedad.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Destruye el identificador único de esta propiedad.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Devuelve el número de visores personalizados con los que se puede ver esta propiedad.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Devuelve la lista de visores personalizados con los que se puede ver esta propiedad.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Establece el valor de esta propiedad y devuelve un mensaje de error si se produjo algún problema.|

## <a name="remarks"></a>Notas
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) es el método preferido para que el administrador de depuración de sesión (SDM) establezca el valor de una propiedad.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
