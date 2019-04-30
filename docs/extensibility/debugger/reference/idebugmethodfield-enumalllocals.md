---
title: IDebugMethodField::EnumAllLocals | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbc610dad6ab5915efe07718ad9a80592af4034
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872995"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crea un enumerador para todas las variables locales del método, las generadas internamente mediante un compilador incluyendo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

#### <a name="parameters"></a>Parámetros
 `pAddress`

 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa una dirección de depuración dentro del método, que apunta a un ámbito concreto o un contexto del objeto.

 `ppLocals`

 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de todas las variables locales en el ámbito especificado; en caso contrario, devuelve un valor null que indica sin asignaciones locales.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún variables locales. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Se enumeran solo las variables definidas dentro del bloque que contiene la dirección de depuración especificado. Este método incluye a las variables locales generadas por el compilador. Si todo lo que es necesario son las variables locales definidas explícitamente en el origen, llamada la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.

 Un método puede contener varios contextos o bloques de ámbito.

## <a name="see-also"></a>Vea también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)