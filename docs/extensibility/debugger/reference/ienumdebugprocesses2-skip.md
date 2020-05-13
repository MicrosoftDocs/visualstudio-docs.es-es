---
title: IEnumDebugProcesses2::Skip ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0e2cfee9c8cc0a8b2eecc745a29244016545ed3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715768"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
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
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` `celt` si es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el final y `S_FALSE` se devuelve.

## <a name="see-also"></a>Vea también
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
