---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727065"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Esta interfaz describe un método.

## <a name="syntax"></a>Sintaxis

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Esta interfaz es una especialización que presenta un método.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de la interfaz [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_METHOD` . Además, los métodos, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)y [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), devuelven la `IDebugMethodField` interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de las interfaces [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Crea un enumerador para los parámetros del método.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Obtiene el puntero "this" del objeto que contiene el método.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Crea un enumerador para todas las variables locales del método.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Crea un enumerador para las variables locales seleccionadas del método.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Determina si se ha definido un atributo personalizado específico.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Crea un enumerador para las variables locales estáticas del método.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Obtiene el contenedor global del método.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Crea un enumerador para el tipo de cada argumento necesario para llamar al método.|

## <a name="remarks"></a>Observaciones
 Un método puede contener parámetros y variables locales.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
