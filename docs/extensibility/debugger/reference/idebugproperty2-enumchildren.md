---
title: IDebugProperty2::EnumChildren ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721509"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera una lista de los elementos secundarios de la propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
[en] Una combinación de indicadores de la [enumeración DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica qué campos de las estructuras [de DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) enumeradas se deben rellenar.

`dwRadix`\
[en] Especifica el radio que se utilizará para dar formato a cualquier información numérica.

`guidFilter`\
[en] GUID del filtro utilizado `dwAttribFilter` `pszNameFilter` con los `DEBUG_PROPERTY_INFO` parámetros y para seleccionar qué elementos secundarios se van a enumerar. Por ejemplo, `guidFilterLocals` filtros para variables locales.

`dwAttribFilter`\
[en] Una combinación de indicadores de la [enumeración DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeración `DBG_ATTRIB_METHOD` que especifica qué tipo de objetos enumerar, por ejemplo, para todos los métodos que podrían ser secundarios de esta propiedad. Se utiliza en `guidFilter` `pszNameFilter` combinación con los parámetros y.

`pszNameFilter`\
[en] El nombre del filtro `guidFilter` utilizado `dwAttribFilter` con los `DEBUG_PROPERTY_INFO` parámetros y para seleccionar qué elementos secundarios se van a enumerar. Por ejemplo, establecer este parámetro en filtros "MyX" para todos los elementos secundarios con el nombre "MyX."

`dwTimeout`\
[en] Especifica el tiempo máximo, en milisegundos, que se debe esperar antes de volver de este método. Se `INFINITE` usa para esperar indefinidamente.

`ppEnum`\
[fuera] Devuelve un [iEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene una lista de las propiedades secundarias.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve código de error.

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
