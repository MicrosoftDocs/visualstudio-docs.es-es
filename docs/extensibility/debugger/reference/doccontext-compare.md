---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
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
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "Enumeración DOCCONTEXT_COMPARE"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica los criterios para comparar dos contextos de documento.  
  
## Sintaxis  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## Members  
 DOCCONTEXT\_EQUAL  
 Busque el primer contexto del documento en la lista que es igual al contexto del documento de destino.  
  
 DOCCONTEXT\_LESS\_THAN  
 Busque el primer contexto del documento en la lista que es menor que el contexto del documento de destino.  
  
 DOCCONTEXT\_GREATER\_THAN  
 Busque el primer contexto del documento en la lista que es mayor que el contexto del documento de destino.  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 Busque el primer contexto del documento en la lista que está en el mismo documento que el contexto del documento de destino.  
  
## Comentarios  
 Pasado como argumento al método de [Comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .  
  
 Estos valores se utilizan para especificar los criterios de una comparación para encontrar el primer contexto de documento en una lista.  Un contexto del documento se proporciona una lista de contextos de documento para compararse con con el método de `IDebugDocumentContext2::Compare` .  El primer contexto del documento en la lista para la cual el operador de comparación es `true` se devuelve.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)