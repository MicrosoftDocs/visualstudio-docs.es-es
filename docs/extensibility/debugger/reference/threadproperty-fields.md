---
title: "THREADPROPERTY_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTY_FIELDS"
helpviewer_keywords: 
  - "Enumeración THREADPROPERTY_FIELDS"
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información sobre un subproceso debe recuperar.  
  
## Sintaxis  
  
```cpp#  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```c#  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Members  
 TPF\_ID  
 Inicializa y usan el campo de `dwThreadId` de la estructura de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) .  
  
 TPF\_SUSPENDCOUNT  
 Inicializa y usan el campo de `dwSuspendCount` de la estructura de s para `THREADPROPERTIE`.  
  
 TPF\_STATE  
 Inicializa y usan el campo de `dwThreadState` de la estructura de s para `THREADPROPERTIE`.  
  
 TPF\_PRIORITY  
 Inicializa y usan el campo de `bstrPriority` de la estructura de s para `THREADPROPERTIE`.  
  
 TPF\_NAME  
 Inicializa y usan el campo de `bstrName` de la estructura de s para `THREADPROPERTIE`.  
  
 TPF\_LOCATION  
 Inicializa y usan el campo de `bstrLocation` de la estructura de s para `THREADPROPERTIE`.  
  
 TPF\_ALLFIELDS  
 especifica todos los campos.  
  
## Comentarios  
 Estos valores se pasan como argumento al método de [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) para indicar qué campos de la estructura de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) se deben inicializar.  
  
 Esta configuración también se utilizan en el miembro de `dwFields` de la estructura de `THREADPROPERTIES` para indicar qué campos son utilizados y válidos.  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)