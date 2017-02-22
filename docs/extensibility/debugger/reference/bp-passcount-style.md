---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
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
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "Estructura BP_PASSCOUNT_STYLE"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la condición asociada con el número de paso de punto de interrupción que hace que el punto de interrupción que éste se active.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Members  
 BP\_PASSCOUNT\_NONE  
 No especifica ningún estilo de recuento de paso de punto de interrupción.  
  
 BP\_PASSCOUNT\_EQUAL  
 Establece el estilo del recuento del paso de punto de interrupción es igual a.  El punto de interrupción se desencadena cuando el número de veces que el punto de interrupción es igual alcanzan el recuento del paso.  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 Establece el estilo de recuento de paso de puntos de interrupción para igual o mayor.  El punto de interrupción se desencadena cuando el número de veces que el punto de interrupción es igual o mayor que el número de pasos.  
  
 BP\_PASSCOUNT\_MOD  
 Especifica un recuento del paso del módulo.  Por ejemplo, si el recuento del paso es de tipo `BP_PASSCOUNT_MOD` y el valor de recuento de paso es 4, el punto de interrupción se desencadena cada vez que el número de llamadas es un múltiplo de 4.  
  
## Comentarios  
 utilizado para el miembro de `stylePassCount` de la estructura de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que es a su vez un miembro de las estructuras de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)