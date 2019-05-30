---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 241db5db55897932120b3253ff5185cb852ea77b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351202"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> EN DESUSO. NO USE.

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

Siempre debe devolver una implementación `E_NOTIMPL`.

## <a name="remarks"></a>Comentarios

> [!WARNING]
> A partir de Visual Studio 2005, ya no se usa este método y siempre debe devolver `E_NOTIMPL`.

Este método se llama cuando el depurador se cierra inesperadamente. Cuando se llama a este método, la DE debe reanudarse el programa como si el usuario separa de él. No hay más eventos de depuración se deben enviar. El programa debe estar en un estado donde adjuntable desde otra instancia del depurador.

## <a name="see-also"></a>Vea también

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)