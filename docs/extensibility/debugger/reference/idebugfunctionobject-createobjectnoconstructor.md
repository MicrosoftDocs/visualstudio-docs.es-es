---
title: IDebugFunctionObject::CreateObjectNoConstructor ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728575"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Crea un objeto sin constructor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`pClassObject`\
[en] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa el tipo del objeto que se va a crear.

`ppObject`\
[fuera] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que representa una instancia de una estructura o tipo complejo (que no requiere un constructor) que es un parámetro para la función que se representa mediante el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.

 Si el parámetro object requiere un constructor, llame a la [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) método.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
