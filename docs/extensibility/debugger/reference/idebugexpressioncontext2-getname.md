---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20004fd424bbb394c4c6d0a80df94d408e86285c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706527"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Recupera el nombre del contexto de evaluación.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

#### <a name="parameters"></a>Parámetros
 `pbstrName`

 [out] Devuelve el nombre del contexto de evaluación.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El nombre es la descripción de este contexto de evaluación. Normalmente, es algo que se puede analizar un evaluador de expresiones que hace referencia a este contexto de evaluación exacta. Por ejemplo, en C++ el nombre es como sigue:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Vea también
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)