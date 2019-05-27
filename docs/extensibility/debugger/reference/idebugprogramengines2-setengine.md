---
title: IDebugProgramEngines2::SetEngine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42b49db266f9c27504a4627506b6652019e2dcf7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211138"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Indica el nodo de programa o un programa qué motor de depuración (DE) a usar para depurar este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parámetros
`guidEngine`\
[in] El GUID de la DE.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)