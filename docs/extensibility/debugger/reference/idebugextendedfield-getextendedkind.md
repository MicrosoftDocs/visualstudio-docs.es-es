---
title: IDebugExtendedField::GetExtendedKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b95992bdb9a35edbb828f05f4d4aad5e7d8631e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352699"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Recupera el tipo de campo extendidas especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetExtendedKind(
   FIELD_KIND_EX* pdwKind
);
```

```csharp
int GetExtendedKind(
   ref enum_FIELD_KIND_EX pdwKind
);
```

## <a name="parameters"></a>Parámetros
`pdwKind`\
[in, out] Valor de la [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) enumeración que define el tipo de campo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)