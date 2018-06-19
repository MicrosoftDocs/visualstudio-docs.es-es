---
title: IDebugProgramNode2::GetHostMachineName_V7 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2adc7125c79afc6b9ebc16b6c4b36f5c147bcdfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115400"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> EN DESUSO. NO UTILICE.

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
[out] Devuelve el nombre de la máquina en la que se ejecuta el programa.

## <a name="return-value"></a>Valor devuelto

Siempre debe devolver una implementación `E_NOTIMPL`.

## <a name="remarks"></a>Comentarios

> [!WARNING]
> A partir de Visual Studio 2005, este método ya no se utiliza y siempre debe devolver `E_NOTIMPL`.

## <a name="see-also"></a>Vea también

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)