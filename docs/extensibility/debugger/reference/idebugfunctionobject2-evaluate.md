---
title: IDebugFunctionObject2::Evaluate ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728439"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Llama a la función y devuelve el valor resultante como un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parámetros
`ppParams`\
[en] Matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representa los parámetros de entrada. Cada uno de estos parámetros se creó mediante uno de los Create métodos en esta interfaz.

`dwParams`\
[en] El número de `ppParams` parámetros de la matriz.

`dwEvalFlags`\
[en] Combinación de indicadores de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifican cómo se va a realizar la evaluación.

`dwTimeout`\
[en] Especifica el tiempo máximo, en milisegundos, que se debe esperar antes de volver de este método. Utilice **INFINITE** para esperar indefinidamente.

`ppResult`\
[fuera] Devuelve un **IDebugObject** que representa el valor de la función como un objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
