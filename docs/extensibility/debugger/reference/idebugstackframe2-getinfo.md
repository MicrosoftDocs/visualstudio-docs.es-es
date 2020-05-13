---
title: IDebugStackFrame2::GetInfo Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09768fc58640d79a3b5628bafc16b2267f1f8a4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719716"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Obtiene una descripción del marco de pila.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFieldSpec`\
[en] Una combinación de indicadores de la [enumeración FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica qué campos del `pFrameInfo` parámetro se deben rellenar.

`nRadix`\
[en] El radio que se utilizará para dar formato a cualquier información numérica.

`pFrameInfo`\
[fuera] Estructura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que se rellena con la descripción del marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
