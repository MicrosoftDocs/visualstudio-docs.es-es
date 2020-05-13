---
title: IDebugProgram2::CanDetach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d03d942bbc052a7ac6bebc6a89c55ec21a1b4c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723127"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina si un motor de depuración (DE) puede separarse del programa.

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
 Si se puede `S_OK`separar, devuelve ; de lo contrario, devuelve un código de error. Devuelve `S_FALSE` si el DE no se puede separar del programa.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
