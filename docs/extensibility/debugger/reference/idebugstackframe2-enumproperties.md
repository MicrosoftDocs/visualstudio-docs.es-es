---
title: IDebugStackFrame2::EnumProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba4cf74c41d321cc03684ec6717a9eea74e9a622
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321854"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Crea un enumerador para las propiedades asociadas con el marco de pila, como las variables locales.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`dwFieldSpec`\
[in] Una combinación de marcas de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica qué campos de los enumerados [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) son estructuras que deben rellenarse.

`nRadix`\
[in] La base que se usará para dar formato a cualquier información numérica.

`refiid`\
[in] Un GUID de un filtro usado para seleccionar qué [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) son estructuras que hay que enumerar, tales como `guidFilterLocals`.

`dwTimeout`\
[in] Tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.

`pcelt`\
[out] Devuelve el número de propiedades enumerados. Esto equivale a llamar a la [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) método.

`ppEnum`\
[out] Devuelve un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene una lista de las propiedades deseadas.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Dado que este método permite seleccionadas todas las propiedades que se recuperan con una sola llamada, es más rápido que secuencialmente una llamada a la [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) y [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) métodos.

## <a name="see-also"></a>Vea también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)