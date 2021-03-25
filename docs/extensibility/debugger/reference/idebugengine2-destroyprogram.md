---
description: Informa a un motor de depuración (DE) que el programa especificado ha finalizado de forma atípica y que el DE debe limpiar todas las referencias al programa y enviar un evento DE destrucción de programas.
title: IDebugEngine2::D estroyProgram | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0a58dd5893c3235ded9c7eeb5f5d47e3ddcb380
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093852"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa a un motor de depuración (DE) que el programa especificado ha finalizado de forma atípica y que el DE debe limpiar todas las referencias al programa y enviar un evento DE destrucción de programas.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

## <a name="parameters"></a>Parámetros
`pProgram`\
de Un objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que ha finalizado de atípica.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Después DE llamar a este método, DE vuelve a enviar un evento [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) al administrador de depuración de la sesión (SDM).

 Este método no está implementado (devuelve `E_NOTIMPL` ) si el de se ejecuta en el mismo proceso que el programa que se está depurando. Este método solo se implementa si el DE se ejecuta en el mismo proceso que el SDM.

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
