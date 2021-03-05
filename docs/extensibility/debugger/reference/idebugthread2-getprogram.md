---
description: Obtiene el programa en el que se está ejecutando un subproceso.
title: 'IDebugThread2:: GetProgram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd58ffb9cbcfd073d20643c4702194759f6267a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164596"
---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
Obtiene el programa en el que se está ejecutando un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProgram ( 
   IDebugProgram2** ppProgram
);
```

```csharp
int GetProgram ( 
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>Parámetros
`ppProgram`\
enuncia Devuelve un objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en el que se ejecuta este subproceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
