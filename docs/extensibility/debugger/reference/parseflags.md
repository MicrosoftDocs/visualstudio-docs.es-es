---
title: PARSEFLAGS | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 28459d2bd5aedb6a3735cf8dcc10ff082c325daa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831409"
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
  
## <a name="members"></a>Miembros  
 PARSE_EXPRESSION  
 Indica que la expresión no es una instrucción.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica que es la expresión que se puede analizar (y más adelante se evalúen) como una dirección.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica que la expresión se analiza durante el tiempo de diseño (es decir, cuando un diseñador está abierto).  
  
## <a name="remarks"></a>Comentarios  
 Pasado como parámetro a la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)