---
title: "THREADPROPERTIES | Microsoft Docs"
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
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "Estructura THREADPROPERTIES"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe las propiedades de un subproceso.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Members  
 dwFields  
 Una combinación de marcadores de enumeración de [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , describe qué campos de esta estructura son válidos.  
  
 dwThreadId  
 El identificador de subproceso  
  
 dwSuspendCount  
 El valor de suspensión del subproceso.  
  
 dwThreadState  
 Un valor de enumeración de [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) que indica el estado de subproceso de ejecución.  
  
 bstrPriority  
 Una cadena que especifica la prioridad de subproceso; por ejemplo, “por encima de lo normal”, “normal”, o “tiempo crítico”.  
  
 bstName  
 El nombre del subproceso.  
  
 bstrLocation  
 La ubicación del subproceso \(normalmente el marco de pila superior\), expresado normalmente como el nombre del método donde se detuvo la ejecución actualmente.  
  
## Comentarios  
 Esta estructura es completa por una llamada al método de [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) .  La información devuelta por se usa normalmente en rellenar la ventana de **Subprocesos** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)