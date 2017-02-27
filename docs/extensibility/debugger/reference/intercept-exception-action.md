---
title: "INTERCEPT_EXCEPTION_ACTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION"
helpviewer_keywords: 
  - "Enumeración INTERCEPT_EXCEPTION_ACTION"
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué acciones para tomar el interceptar las excepciones.  
  
## Sintaxis  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```c#  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### Parámetros  
 IEA\_INTERCEPT  
 permisos que interceptan la excepción actual.  Éste es el único valor compatible actualmente y debe especificarse.  
  
## Comentarios  
 estos valores se pasan en el método de [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)