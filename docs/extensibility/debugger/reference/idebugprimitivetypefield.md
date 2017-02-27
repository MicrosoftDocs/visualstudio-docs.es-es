---
title: "IDebugPrimitiveTypeField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugPrimitiveTypeField"
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa un valor de enumeración de tipo primitivo de una interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Sintaxis  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## Métodos  
 Además de los métodos de la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Recupera el tipo primitivo asociado a este campo.|  
  
## Requisitos  
 encabezado: Sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll