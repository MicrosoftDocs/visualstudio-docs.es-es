---
title: IDebugProcessSecurity::QueryCanSafelyAttach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723199"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Este método permite al proveedor de puertos mostrar una advertencia antes de que el usuario se conecte a un proceso no seguro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valor devuelto
 Los valores devueltos son los siguientes:

- `S_OK`: La conexión al proceso es segura y no se muestra ningún cuadro de diálogo de advertencia.

- `S_FALSE`: La conexión podría ser un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.

- `FAILURE`: La fijación al proceso falla.

## <a name="see-also"></a>Vea también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
