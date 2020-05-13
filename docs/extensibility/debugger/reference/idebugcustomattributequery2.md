---
title: IDebugCustomAttributeQuery2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732492"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina la existencia de un atributo personalizado para este campo y, si existe, devuelve la información del atributo.

## <a name="syntax"></a>Sintaxis

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para admitir atributos personalizados.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de la **IDebugCustomAttributeQuery** interfaz.

|Método|Descripción|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina si existe un atributo personalizado por nombre.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Obtiene la información de atributo para el atributo personalizado especificado.|

 Además de los métodos `IDebugCustomAttributeQuery2` **IDebugCustomAttributeQuery,** implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Obtiene un enumerador para todos los atributos personalizados asociados a este campo.|

## <a name="remarks"></a>Observaciones
 El [Método IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) puede devolver un enumerador para todos los atributos personalizados definidos para este campo.

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
