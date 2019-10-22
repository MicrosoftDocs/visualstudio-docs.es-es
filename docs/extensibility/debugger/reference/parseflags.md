---
title: PARSEFLAGS | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6123c6438defff596351fff3d1ba31ea52a19f28
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349934"
---
# <a name="parseflags"></a>PARSEFLAGS
Especifica cómo analizar una expresión.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Campos
 `PARSE_EXPRESSION`\
 Indica que la expresión no es una instrucción.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indica que es la expresión que se puede analizar (y más adelante se evalúen) como una dirección.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indica que la expresión se analiza durante el tiempo de diseño (es decir, cuando un diseñador está abierto).

## <a name="remarks"></a>Comentarios
 Pasado como parámetro a la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)