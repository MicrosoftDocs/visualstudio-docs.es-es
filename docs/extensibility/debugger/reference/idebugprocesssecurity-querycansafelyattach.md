---
description: Este método permite al proveedor del puerto mostrar una advertencia antes de que el usuario se adjunte a un proceso no seguro.
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
ms.openlocfilehash: 0e6a586983d64e8be27b15a0514234d1a321e943
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166169"
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

## <a name="see-also"></a>Consulte también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
