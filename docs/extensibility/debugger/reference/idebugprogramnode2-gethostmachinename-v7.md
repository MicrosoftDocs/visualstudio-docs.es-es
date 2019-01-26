---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0228d718377f6bd43ae44b44fb44900e4526d3b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990711"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> EN DESUSO. NO USE.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>Parámetros

`pbstrHostMachineName`  
[out] Devuelve el nombre de la máquina en que se ejecuta el programa.

## <a name="return-value"></a>Valor devuelto

Siempre debe devolver una implementación `E_NOTIMPL`.

## <a name="remarks"></a>Comentarios

> [!WARNING]
> A partir de Visual Studio 2005, ya no se usa este método y siempre debe devolver `E_NOTIMPL`.

## <a name="see-also"></a>Vea también

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)