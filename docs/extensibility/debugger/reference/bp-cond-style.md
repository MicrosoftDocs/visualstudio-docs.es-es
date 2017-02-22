---
title: "BP_COND_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "Enumeración BP_COND_STYLE"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el estilo de la condición de punto de interrupción para los puntos de interrupción pendientes y enlazados.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Members  
 BP\_COND\_NONE  
 Desencadena el punto de interrupción cuando se alcanza la posición del punto de interrupción.  Ninguna condición de punto de interrupción especificada.  
  
 BP\_COND\_WHEN\_TRUE  
 Desencadena el punto de interrupción solo cuando la expresión condicional asociado al punto de interrupción se evalúa como `true`.  
  
 BP\_COND\_WHEN\_CHANGED  
 Desencadena el punto de interrupción sólo cuando el valor de la expresión condicional asociado al punto de interrupción ha cambiado su evaluación anterior.  
  
## Comentarios  
 utilizado para el miembro de `styleCondition` de la estructura de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)