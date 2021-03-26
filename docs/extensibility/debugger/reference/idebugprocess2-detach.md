---
description: Desasocia el depurador de este proceso desasociando todos los programas del proceso.
title: IDebugProcess2::D Etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d75f9dd58e2a26f6d465fc93988fa3d3785a0d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071667"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Desasocia el depurador de este proceso desasociando todos los programas del proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Todos los programas y el proceso continúan ejecutándose, pero ya no forman parte de la sesión de depuración. Una vez completada la operación de desasociación, no se enviarán más eventos de depuración para este proceso (y sus programas).

## <a name="see-also"></a>Consulte también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
