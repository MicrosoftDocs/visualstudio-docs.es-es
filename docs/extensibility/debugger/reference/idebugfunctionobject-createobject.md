---
description: Crea un objeto utilizando un constructor.
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8870910e01f2afa5bff6eac461d6e80f35e6a7e0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150047"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Crea un objeto utilizando un constructor.

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
de Objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa el constructor del objeto que se va a crear.

`dwArgs`\
de Número de parámetros de la `pArg` matriz. Representa el número de parámetros pasados al constructor.

`pArg`\
de Matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representan los parámetros pasados al constructor.

`ppObject`\
enuncia Devuelve un `IDebugObject` que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que represente una instancia de una clase (u otro tipo complejo que requiera un constructor) que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Si el parámetro de objeto no requiere un constructor, llame al método [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .

## <a name="see-also"></a>Consulte también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
