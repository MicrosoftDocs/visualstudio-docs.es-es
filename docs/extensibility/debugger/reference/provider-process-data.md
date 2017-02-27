---
title: "PROVIDER_PROCESS_DATA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_PROCESS_DATA"
helpviewer_keywords: 
  - "Estructura PROVIDER_PROCESS_DATA"
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura proporciona información sobre los procesos que se ejecutan en un equipo.  
  
## Sintaxis  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```c#  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## Members  
 Campos  
 Una combinación de marcadores de enumeración de [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , indicando se completan los campos.  
  
 ProgramNodes  
 Una estructura de [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) que contiene una matriz de nodos del programa.  
  
 fIsDebuggerPresent  
 Cero \(`TRUE`\) si el depurador de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ejecuta, cero \(`FALSE`\) si no es.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) donde se completa.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)