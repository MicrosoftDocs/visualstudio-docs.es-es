---
description: Recupera el objeto que representa el motor DE depuración recién creado (DE).
title: 'IDebugEngineCreateEvent2:: GetEngine | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2::GetEngine
helpviewer_keywords:
- IDebugEngineCreateEvent2::GetEngine
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aaabac0b9ee0e6fb2e8982d673e8e55e1cede4e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153681"
---
# <a name="idebugenginecreateevent2getengine"></a>IDebugEngineCreateEvent2::GetEngine
Recupera el objeto que representa el motor DE depuración recién creado (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetEngine( 
   IDebugEngine2** pEngine
);
```

```csharp
int GetEngine( 
   out IDebugEngine2 pEngine
);
```

## <a name="parameters"></a>Parámetros
`pEngine`\
enuncia Devuelve un objeto [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) que representa el objeto de la nueva creación de.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
