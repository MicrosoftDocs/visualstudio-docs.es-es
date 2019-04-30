---
title: IEnumDebugPropertyInfo2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae1e87ad302cbd25fcda691b47372f4fbd5d1771
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866062"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
Devuelve el siguiente conjunto de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Next(
   ULONG                 celt,
   DEBUG_PROPERTY_INFO** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   DEBUG_PROPERTY_INFO[] rgelt,
   ref uint              pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 `celt`

 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.

 `rgelt`

 [in, out] Matriz de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) elementos que deben rellenarse.

 `pceltFetched`

 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)