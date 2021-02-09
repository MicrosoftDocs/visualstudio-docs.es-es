---
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2c47f51fb0ddc47218b11fe5673e0ede8362ff89
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921081"
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
de Objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el tipo del objeto que se va a crear.

`ppObject`\
enuncia Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Llame a este método para crear un objeto que represente una instancia de una estructura o un tipo complejo (que no requiere un constructor) que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Si el parámetro de objeto requiere un constructor, llame al método [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [DataSpace](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
