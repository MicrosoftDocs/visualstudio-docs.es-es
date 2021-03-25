---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
description: Este método es una forma antigua y en desuso del método detach usado antes de Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16630be49dd884f8bcc82da2fead158eb3a25e5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053560"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> En desuso. NO USE.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valor devuelto

Una implementación siempre debe devolver `E_NOTIMPL` .

## <a name="remarks"></a>Observaciones

> [!WARNING]
> A partir de Visual Studio 2005, este método ya no se usa y siempre debe devolver `E_NOTIMPL` .

Se llama a este método cuando el depurador se cierra inesperadamente. Cuando se llama a este método, el DE debe reanudar el programa como si el usuario lo desasociara. No se deben enviar más eventos de depuración. El programa debe estar en un estado en el que se pueda adjuntar desde otra instancia del depurador.

## <a name="see-also"></a>Consulte también

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
