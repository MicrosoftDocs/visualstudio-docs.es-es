---
title: IEnumDebugPropertyInfo2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715352"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Esta interfaz enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar información para una propiedad determinada.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener esta interfaz que representa a los elementos secundarios de una propiedad determinada. Llame a [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para obtener esta interfaz que representa las propiedades de un marco de pila determinado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugPropertyInfo2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un número especificado de [estructuras de DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Omite un número especificado de [estructuras de DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Obtiene el número de [estructuras DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) de un enumerador.|

## <a name="remarks"></a>Observaciones
 En general, una propiedad es una jerarquía de información que puede incluir un nombre, valor, dirección y tipo, así como cualquier otra información adecuada para el objeto de propiedad asociado o el marco de pila. Vea [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para obtener más detalles.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
