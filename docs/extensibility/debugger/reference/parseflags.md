---
title: PARSEFLAGS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 70766aef19c199a191f141947f1b5a458450c322
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="parseflags"></a>PARSEFLAGS
Especifica cómo analizar una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Miembros  
 PARSE_EXPRESSION  
 Indica que la expresión no es una instrucción.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica que la expresión se analiza (y más adelante se evalúan) como una dirección.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica que se está analizando la expresión en tiempo de diseño (es decir, cuando un diseñador abierto).  
  
## <a name="remarks"></a>Comentarios  
 Pasar como un parámetro a la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)