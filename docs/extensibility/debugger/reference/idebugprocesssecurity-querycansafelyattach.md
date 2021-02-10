---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3f2c02610b5fbe99335ccea6d7c566a0fe58df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931466"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Este método permite al proveedor del puerto mostrar una advertencia antes de que el usuario se adjunte a un proceso no seguro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valor devuelto
 Los valores devueltos son los siguientes:

- `S_OK`: La asociación al proceso es segura y no se muestra ningún cuadro de diálogo de advertencia.

- `S_FALSE`: La asociación puede ser un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.

- `FAILURE`: No se puede asociar al proceso.

## <a name="see-also"></a>Vea también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
