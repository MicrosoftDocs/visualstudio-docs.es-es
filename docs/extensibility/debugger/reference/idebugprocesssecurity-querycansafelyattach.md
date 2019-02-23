---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701438"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Este método permite que el proveedor del puerto mostrar una advertencia antes de que el usuario se une a un proceso no seguro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valor devuelto
 Los valores devueltos son como sigue:

-   `S_OK`: Asociar al proceso es seguro y no se muestra ningún cuadro de diálogo de advertencia.

-   `S_FALSE`: Asociar podría ser un problema de seguridad y se muestra un cuadro de diálogo con una advertencia.

-   `FAILURE`: No se puede asociar al proceso.

## <a name="see-also"></a>Vea también
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)