---
title: 'IDebugFunctionObject2:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728481"
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

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
