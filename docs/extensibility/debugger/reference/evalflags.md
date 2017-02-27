---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "Enumeración EVALFLAGS"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica marcadores que controlan la evaluación de la expresión.  
  
## Sintaxis  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## Members  
 EVAL\_RETURNVALUE  
 Especifica que el valor devuelto, si existe, se evalúa.  
  
 EVAL\_NOSIDEEFFECTS  
 especifica que los efectos secundarios para no ser permitido.  
  
 EVAL\_ALLOWBPS  
 Especifica detenerse en los puntos de interrupción.  
  
 EVAL\_ALLOWERRORREPORT  
 Especifica el informe de errores al host que se permitirá.  Se utiliza principalmente para la evaluación de expresiones en script en Internet Explorer.  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 Convierte las funciones que se evaluarán como direcciones, en lugar de invocar la función.  
  
 EVAL\_NOFUNCEVAL  
 Impide que la función sea evaluada.  por ejemplo, considere el símbolo de `int` en la expresión `myExpression(int) + 10`.  esta función se puede correctamente evaluar como dirección, pero no como valor.  
  
 EVAL\_NOEVENTS  
 Marca para indicar que los eventos que se producen durante la evaluación de la expresión no se deberían enviar al administrador \(SDM\) de depuración de la sesión o al IDE.  
  
## Comentarios  
 Estos marcadores se pasan como argumentos a los métodos de [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) y de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .  
  
 Estos marcadores pueden combinarse con una operación OR bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)