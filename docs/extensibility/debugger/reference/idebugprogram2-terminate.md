---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b80afe3f0061e016301b86229f2eacedf217a43
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709309"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Finaliza el programa.

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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si es posible, el programa se termina y descarga desde el proceso; en caso contrario, el motor de depuración (DE) llevará a cabo cualquier limpieza necesaria.

 Este método o el [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) se llama al método por el IDE, normalmente en respuesta al usuario Detener depuración todas. La implementación de este método Idealmente, debería, finalizar el programa dentro del proceso. Si esto no es posible, el DE debe evitar que el programa se ejecute más en este proceso (y realizar cualquier limpieza necesaria). Si el `IDebugProcess2::Terminate` se llamó al método por el IDE, todo el proceso se terminará después el `IDebugProgram2::Terminate` se llama al método.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)