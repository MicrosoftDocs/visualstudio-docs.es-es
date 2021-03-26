---
description: Recupera el nombre del contexto de evaluación.
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3aa27ba70e0b407e72a42d2904467ee85fc027b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092324"
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
enuncia Devuelve el nombre del contexto de evaluación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El nombre es la descripción de este contexto de evaluación. Normalmente es algo que un evaluador de expresiones que hace referencia a este contexto de evaluación exacto puede analizarlo. Por ejemplo, en C++, el nombre es el siguiente:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Consulte también
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
