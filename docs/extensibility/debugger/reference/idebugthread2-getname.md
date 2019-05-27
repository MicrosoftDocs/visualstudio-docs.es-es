---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4da4f3287d8d307dd65aff5d09aa34c5b17b0119
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199650"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtiene el nombre de un subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parámetros
`pbstrName`\
[out] Devuelve el nombre del subproceso.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El nombre recuperado siempre es un nombre que se puede mostrar y este nombre describe el subproceso. El nombre del subproceso puede derivarse de una arquitectura de tiempo de ejecución que admite denominado subprocesos, o podría ser un nombre derivado el motor de depuración. Como alternativa, se puede establecer el nombre del subproceso mediante una llamada a la [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) método.

## <a name="see-also"></a>Vea también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)