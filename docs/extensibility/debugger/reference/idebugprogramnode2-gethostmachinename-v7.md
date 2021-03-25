---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft Docs'
description: Este es el método obsoleto para obtener el nombre de la máquina host que se usó antes de Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20d62c180848c4875fa3312e0194ebdb467a93ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053547"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> En desuso. NO USE.

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

## <a name="parameters"></a>Parámetros

`pbstrHostMachineName`\
enuncia Devuelve el nombre del equipo en el que se ejecuta el programa.

## <a name="return-value"></a>Valor devuelto

Una implementación siempre debe devolver `E_NOTIMPL` .

## <a name="remarks"></a>Observaciones

> [!WARNING]
> A partir de Visual Studio 2005, este método ya no se usa y siempre debe devolver `E_NOTIMPL` .

## <a name="see-also"></a>Consulte también

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
