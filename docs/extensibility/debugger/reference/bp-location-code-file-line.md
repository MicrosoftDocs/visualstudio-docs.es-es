---
title: "BP_LOCATION_CODE_FILE_LINE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FILE_LINE"
helpviewer_keywords: 
  - "Estructura BP_LOCATION_CODE_FILE_LINE"
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene los datos para la ubicación de un punto de interrupción en una línea determinada de un archivo de origen de código.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## Members  
 `bstrContext`  
 El contexto de punto de interrupción, normalmente un nombre de método o de función como se explica en una pila de llamadas.  
  
 `pDocPos`  
 El objeto de [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) que representa la posición del documento de punto de interrupción.  
  
## Comentarios  
 Esta estructura es miembro de la estructura de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)