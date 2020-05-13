---
title: PARSEFLAGS ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714118"
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

## <a name="fields"></a>Fields
 `PARSE_EXPRESSION`\
 Indica que la expresión no es una instrucción.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indica que la expresión se va a analizar (y evaluar posteriormente) como una dirección.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indica que la expresión se está analizando durante el tiempo de diseño (es decir, cuando un diseñador está abierto).

## <a name="remarks"></a>Observaciones
 Se pasa como parámetro a los métodos [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [Parse.](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
