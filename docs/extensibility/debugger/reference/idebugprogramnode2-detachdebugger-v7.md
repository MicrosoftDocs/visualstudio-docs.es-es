---
title: IDebugProgramNode2::DetachDebugger_V7 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a79c073048fe30a4abed069487ad09943253475
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115036"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> EN DESUSO. NO UTILICE.

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
> A partir de Visual Studio 2005, este método ya no se utiliza y siempre debe devolver `E_NOTIMPL`.

Este método se llama cuando el depurador se cierra inesperadamente. Cuando se llama a este método, la DE debe reanudar el programa como si el usuario se separa del mismo. No hay más eventos de depuración se deben enviar. El programa debe estar en un estado donde resulta adjuntable desde otra instancia del depurador.

## <a name="see-also"></a>Vea también

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)