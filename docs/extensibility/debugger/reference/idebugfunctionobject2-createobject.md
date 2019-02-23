---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7004e57aaf659b90b5323105c6d2c2b80baa4d0f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723128"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Crea un objeto que se utiliza un constructor según los valores de marca de evaluación y un valor de tiempo de espera.

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

#### <a name="parameters"></a>Parámetros
 `pConstructor`

 [in] Un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa el constructor del objeto que se va a crear.

 `dwArgs`

 [in] El número de parámetros en el `pArg` matriz. Representa el número de parámetros pasados al constructor.

 `pArgs`

 [in] Una matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representan los parámetros pasan al constructor.

 `dwEvalFlags`

 [in] Una combinación de marcas de la [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeración que especifican cómo se puede realizar la evaluación.

 `dwTimeout`

 [in] Tiempo máximo, en milisegundos para esperar antes de volver de este método. Use **infinito** para esperar indefinidamente.

 `ppObject`

 [out] Devuelve un **IDebugObject** que representa el objeto recién creado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Llame a este método para crear un objeto que representa una instancia de una clase o de otro tipo complejo que requiere un constructor, que es un parámetro.

## <a name="see-also"></a>Vea también
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)