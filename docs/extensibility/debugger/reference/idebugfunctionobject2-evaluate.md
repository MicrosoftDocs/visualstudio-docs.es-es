---
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b7d69434a6bd6aefb073a252ee35c07fccbee6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920974"
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
de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa los parámetros de entrada. Cada uno de estos parámetros se creó utilizando uno de los métodos Create en esta interfaz.

`dwParams`\
de Número de parámetros de la `ppParams` matriz.

`dwEvalFlags`\
de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica cómo se va a realizar la evaluación.

`dwTimeout`\
de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use **infinita** para esperar indefinidamente.

`ppResult`\
enuncia Devuelve un **IDebugObject** que representa el valor de la función como un objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
