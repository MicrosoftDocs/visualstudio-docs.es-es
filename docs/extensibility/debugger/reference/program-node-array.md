---
title: "PROGRAM_NODE_ARRAY | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROGRAM_NODE_ARRAY"
helpviewer_keywords: 
  - "Estructura PROGRAM_NODE_ARRAY"
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROGRAM_NODE_ARRAY
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene una matriz de objetos que describen los programas de interés.  
  
## Sintaxis  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```c#  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## Members  
 dwCount  
 Número de objetos de la matriz de `Members` .  
  
 Members  
 Matriz de los objetos de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que describen los programas solicitados.  
  
## Comentarios  
 Esta estructura es parte de la estructura de [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) que a su vez es completa por una llamada al método de [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)