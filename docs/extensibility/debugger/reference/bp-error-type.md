---
title: "BP_ERROR_TYPE | Microsoft Docs"
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
  - "BP_ERROR_TYPE"
helpviewer_keywords: 
  - "Enumeración BP_ERROR_TYPE"
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica el tipo de error de un punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```c#  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## Members  
 BPET\_NONE  
 No especifica ningún error de punto de interrupción.  
  
 BPET\_TYPE\_WARNING  
 Especifica un error de punto de interrupción de advertencia\-estilo.  
  
 BPET\_TYPE\_ERROR  
 Especifica un error de punto de interrupción de tipo on error.  
  
 BPET\_SEV\_HIGH  
 Especifica un error de punto de interrupción de la alto\-gravedad.  
  
 BPET\_SEV\_GENERAL  
 Especifica un error de punto de interrupción de la medio\-gravedad.  
  
 BPET\_SEV\_LOW  
 Especifica un error de punto de interrupción de la bajo\-gravedad.  
  
 BPET\_TYPE\_MASK  
 Especifica un error de punto de interrupción de máscara\-estilo.  
  
 BPET\_SEV\_MASK  
 Especifica un error de punto de interrupción de gravedad\-máscara\-estilo.  
  
 BPET\_GENERAL\_WARNING  
 Especifica un error de punto de interrupción de general\-advertencia\-estilo.  
  
 BPET\_GENERAL\_ERROR  
 Especifica un error de punto de interrupción de general\-error\-estilo.  
  
 BPET\_ALL  
 Especifica todos los tipos de error de punto de interrupción.  
  
## Comentarios  
 estos valores se pueden combinar con `OR` bit a bit y utilizar para el miembro de `dwType` de la estructura de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .  Pasado como parámetro al método de [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .  
  
 Constituyen un tipo de error de punto de interrupción de un tipo y una gravedad.  Esto significa que un tipo de error de punto de interrupción nunca es simplemente un tipo \(por ejemplo, `BPET_TYPE_ERROR`,\) o una gravedad \(por ejemplo,`BPET_SEV_GENERAL`\) en sí mismo.  `BPET_GENERAL_WARNING` y `BPET_GENERAL_ERROR` proporcionan los valores predefinidos para los puntos de interrupción generales de advertencias y errores.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)