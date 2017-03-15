---
title: "PARSEFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PARSEFLAGS"
helpviewer_keywords: 
  - "Enumeración PARSEFLAGS"
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# PARSEFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica cómo analizar una expresión.  
  
## Sintaxis  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```c#  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## Members  
 PARSE\_EXPRESSION  
 indica que la expresión no es una instrucción.  
  
 PARSE\_FUNCTION\_AS\_ADDRESS  
 Indica que la expresión debe ser analizada \(y evaluar más adelante\) como dirección.  
  
 PARSE\_DESIGN\_TIME\_EXPR\_EVAL  
 Indica que la expresión se analiza en tiempo de diseño \(es decir, cuando un diseñador está abierto\).  
  
## Comentarios  
 pasado como parámetro a los métodos de [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y de [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)