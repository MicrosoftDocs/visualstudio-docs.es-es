---
description: Este método permite al proveedor del puerto mostrar una advertencia antes de que el usuario se adjunte a un proceso no seguro.
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbbfcf11a35fcfc43ae9e903b13a7480a3cf9743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076282"
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
