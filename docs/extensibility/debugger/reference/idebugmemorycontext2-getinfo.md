---
description: Recupera una estructura de CONTEXT_INFO que describe el contexto.
title: 'IDebugMemoryContext2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87f5dbf14d714f4915e99c23a56b8c9490dd23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058630"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Recupera una estructura de [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) que describe el contexto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
de Combinación de marcas de la enumeración [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) que indican qué campos de la estructura de [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) se van a rellenar.

`pInfo`\
[in, out] `CONTEXT_INFO` Estructura que se rellena.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
