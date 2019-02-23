---
title: IDebugProgram2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc95cee8a463337564ddfec5322ab074e3485bc1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693609"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina si puede separar un motor de depuración (DE) desde el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Valor devuelto
 Si puede desasociar, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `S_FALSE` si no se puede separar la DE desde el programa.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)