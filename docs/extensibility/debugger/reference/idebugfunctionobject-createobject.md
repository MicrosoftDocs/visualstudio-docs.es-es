---
title: IDebugFunctionObject::CreateObject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728596"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crea un objeto mediante un constructor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parámetros
`pConstructor`\
[en] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa el constructor del objeto que se va a crear.

`dwArgs`\
[en] El número de `pArg` parámetros de la matriz. Representa el número de parámetros pasados al constructor.

`pArg`\
[en] Matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representan los parámetros pasados al constructor.

`ppObject`\
[fuera] Devuelve `IDebugObject` un objeto que representa el recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que representa una instancia de una clase (u otro tipo complejo que requiere un constructor) que es un parámetro para la función que se representa mediante el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.

 Si el parámetro object no requiere un constructor, llame a la [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) método.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
