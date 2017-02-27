---
title: "STEPUNIT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPUNIT"
helpviewer_keywords: 
  - "Enumeración STEPUNIT"
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPUNIT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la unidad del paso a paso.  
  
## Sintaxis  
  
```cpp#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```c#  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## Members  
 STEP\_STATEMENT  
 Pasos por instrucción.  
  
 STEP\_LINE  
 Pasos por línea.  
  
 STEP\_INSTRUCTION  
 Pasos por instrucción.  
  
## Comentarios  
 Pasado como argumento al método de [Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md)