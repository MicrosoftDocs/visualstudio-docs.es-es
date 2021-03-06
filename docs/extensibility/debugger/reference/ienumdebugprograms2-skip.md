---
description: Omite el número especificado de elementos de la enumeración programs.
title: 'IEnumDebugPrograms2:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Skip
helpviewer_keywords:
- IEnumDebugPrograms2::Skip
ms.assetid: b283858b-b375-4760-bfec-ab37de89958d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1aa198437a84c0e648897d22bc08c719832e7994
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226064"
---
# <a name="ienumdebugprograms2skip"></a>IEnumDebugPrograms2::Skip
Omite el número de elementos especificado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a omitir.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el final y `S_FALSE` se devuelve.

## <a name="see-also"></a>Consulte también
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
