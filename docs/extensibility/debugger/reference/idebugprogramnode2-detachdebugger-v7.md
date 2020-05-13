---
title: IDebugProgramNode2::DetachDebugger_V7 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722111"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Obsoleto. NO USAR.

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

Una implementación `E_NOTIMPL`siempre debe devolver .

## <a name="remarks"></a>Observaciones

> [!WARNING]
> A partir de Visual Studio 2005, este método `E_NOTIMPL`ya no se usa y siempre debe devolver .

Se llama a este método cuando el depurador se cierra inesperadamente. Cuando se llama a este método, el DE debe reanudar el programa como si el usuario se despropiedad de él. No se deben enviar más eventos de depuración. El programa debe estar en un estado en el que se pueda adjuntar desde otra instancia del depurador.

## <a name="see-also"></a>Vea también

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
