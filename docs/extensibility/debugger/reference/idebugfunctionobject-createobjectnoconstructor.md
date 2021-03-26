---
description: Crea un objeto sin constructor.
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a35cab590ab763a3598f45ebe79543e66c2fa4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073526"
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

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que represente una instancia de una estructura o un tipo complejo (que no requiere un constructor) que sea un parámetro de la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Si el parámetro de objeto requiere un constructor, llame al método [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>Consulte también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [DataSpace](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
