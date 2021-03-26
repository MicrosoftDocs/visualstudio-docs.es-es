---
description: Finaliza el proceso.
title: 'IDebugProcess2:: Terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e26a4486e9c97638d20f9c634b66183824c2b39
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081651"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
Finaliza el proceso.

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
 Cuando finaliza un proceso, se terminan todos los programas de ese proceso. ninguno puede ejecutar más código.

## <a name="see-also"></a>Consulte también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
