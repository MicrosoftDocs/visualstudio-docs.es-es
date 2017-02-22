---
title: "CONSTRUCTOR_ENUM | Microsoft Docs"
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
  - "CONSTRUCTOR_ENUM"
helpviewer_keywords: 
  - "Enumeración CONSTRUCTOR_ENUM"
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# CONSTRUCTOR_ENUM
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Selecciona diferentes tipos de constructores.  
  
## Sintaxis  
  
```cpp#  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```c#  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## Members  
 crAll  
 Selecciona todos los constructores.  
  
 crNonStatic  
 Selecciona constructores estáticos.  
  
 crStatic  
 Selecciona constructores estáticos.  
  
## Comentarios  
 Pasado como argumento al método de [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) .  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)