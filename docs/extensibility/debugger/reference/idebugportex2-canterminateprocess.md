---
title: 'IDebugPortEx2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a8a58b2fc328f5659736e2ceb399bda62dc90cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891103"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Determina si un proceso se puede terminar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>Parámetros
`pPortProcess`\
de Objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso que se va a terminar.

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si se puede terminar el proceso; de lo contrario, devuelve `S_FALSE` .

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
