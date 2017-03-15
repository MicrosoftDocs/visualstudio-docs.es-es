---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "Estructura BP_LOCATION_DATA_STRING"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Se utiliza para establecer los puntos de interrupción de datos basados en una cadena que el usuario puede especificar el entorno de desarrollo integrado \(IDE\).  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## Members  
 `pThread`  
 El objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que el punto de interrupción.  
  
 `bstrContext`  
 El contexto del punto de interrupción en el código, normalmente un nombre de método o de función como se explica en una pila de llamadas.  
  
 `bstrDataExpr`  
 La cadena de los datos que el usuario escribe para establecer el punto de interrupción.  
  
 `dwNumElements`  
 El número de elementos en la cadena de datos en la que el punto de interrupción.  
  
## Comentarios  
 Esta estructura es miembro de la estructura de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)