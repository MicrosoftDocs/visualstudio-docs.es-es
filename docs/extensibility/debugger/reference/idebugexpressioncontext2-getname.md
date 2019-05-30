---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d53d7f497700d4e23587927adc0c2cee37824daa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325877"
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

## <a name="parameters"></a>Parámetros
`pbstrName`\
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