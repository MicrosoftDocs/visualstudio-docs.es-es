---
description: Ejecuta el programa del depurador.
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3d996fd7b8cda1d5e36322c85d49c9889dd66dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146007"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Ejecuta el programa del depurador. El subproceso se devuelve para proporcionar a la información del depurador el subproceso que está viendo el usuario al ejecutar el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parámetros
`pThread`\
de Objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Hay tres formas diferentes de que un depurador pueda reanudar la ejecución después de detenerse:

- Ejecutar: cancele cualquier paso anterior y ejecute hasta el siguiente punto de interrupción, etc.

- Paso: cancelar cualquier paso anterior y ejecutarlo hasta que se complete el nuevo paso.

- Continuar: vuelva a ejecutar y deje cualquier paso anterior activo.

  El subproceso que `ExecuteOnThread` se pasa a es útil a la hora de decidir qué paso cancelar. Si no conoce el subproceso, la ejecución de Execute cancela todos los pasos. Con el conocimiento del subproceso, solo tiene que cancelar el paso en el subproceso activo.

## <a name="see-also"></a>Consulte también
- [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
