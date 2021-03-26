---
description: Finaliza el programa.
title: 'IDebugProgram2:: Terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 404df2be6718ab691ec47081b6fd400a1ddc8891
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084472"
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
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si es posible, el programa se terminará y se descargará del proceso. de lo contrario, el motor DE depuración (DE) realizará cualquier limpieza necesaria.

 El IDE llama a este método o al método [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) , normalmente en respuesta al usuario que detiene toda la depuración. La implementación de este método debería, idealmente, terminar el programa dentro del proceso. Si esto no es posible, el DE debe evitar que el programa se ejecute más en este proceso (y realice cualquier limpieza necesaria). Si el `IDebugProcess2::Terminate` IDE llamó al método, todo el proceso finalizará en algún momento después de `IDebugProgram2::Terminate` llamar al método.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
