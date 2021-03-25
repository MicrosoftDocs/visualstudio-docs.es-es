---
description: Esta interfaz representa un atributo personalizado y puede proporcionar el nombre, el elemento primario y el tipo de clase del atributo.
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b96f4330371e8fb18b75a6ad6f17d61cccd3812
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095438"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Esta interfaz representa un atributo personalizado y puede proporcionar el nombre, el elemento primario y el tipo de clase del atributo.

## <a name="syntax"></a>Sintaxis

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz para admitir atributos personalizados asociados a un símbolo. Normalmente se implementa en su propio objeto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) devuelve esta interfaz. Una llamada al método [enumcustomattributes (](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) devuelve la interfaz [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugCustomAttribute` .

|Método|Descripción|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtiene el campo al que está asociado el atributo actual.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtiene el tipo de clase de atributo personalizado.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtiene el nombre del atributo personalizado.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtiene la información del atributo como un BLOB de bytes.|

## <a name="remarks"></a>Observaciones
 Un atributo personalizado es una estructura para C# que proporciona metadatos personalizados asociados a una clase o un método determinados.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
