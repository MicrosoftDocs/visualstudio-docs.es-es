---
description: Crea un objeto que usa un constructor con valores de marca de evaluación determinados y un valor de tiempo de espera.
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143147"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crea un objeto que usa un constructor con valores de marca de evaluación determinados y un valor de tiempo de espera.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parámetros
`pConstructor`\
de Objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa el constructor del objeto que se va a crear.

`dwArgs`\
de Número de parámetros de la `pArg` matriz. Representa el número de parámetros pasados al constructor.

`pArgs`\
de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa los parámetros pasados al constructor.

`dwEvalFlags`\
de Combinación de marcas de la enumeración [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica cómo se va a realizar la evaluación.

`dwTimeout`\
de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use **infinita** para esperar indefinidamente.

`ppObject`\
enuncia Devuelve un **IDebugObject** que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que represente una instancia de una clase u otro tipo complejo que requiera un constructor, que es un parámetro.

## <a name="see-also"></a>Consulte también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
