---
title: IDebugProgram2::Terminar ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722745"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termina el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si es posible, el programa se terminará y se descargará del proceso; de lo contrario, el motor de depuración (DE) realizará cualquier limpieza necesaria.

 El IDE llama a este método o al método [Terminate,](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) normalmente en respuesta al usuario que detiene toda la depuración. La implementación de este método debería, idealmente, terminar el programa dentro del proceso. Si esto no es posible, el DE debe evitar que el programa se ejecute más en este proceso (y hacer cualquier limpieza necesaria). Si `IDebugProcess2::Terminate` el IDE llamó al método, todo el proceso se `IDebugProgram2::Terminate` terminará en algún momento después de llamar al método.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
