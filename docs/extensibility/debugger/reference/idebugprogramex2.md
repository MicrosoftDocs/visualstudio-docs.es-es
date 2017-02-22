---
title: "IDebugProgramEx2 | Microsoft Docs"
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
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "Interfaz IDebugProgramEx2"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite la asociación de administrador de depuración \(SDM\) de sesión al programa y obtiene el nodo de programa asociado con un programa.  
  
## Sintaxis  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz en el mismo objeto que la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dejar el SDM asociar un programa a la vez permite que el proveedor de puerto siga a todas las sesiones asociadas al programa.  El proveedor de puerto puede implementar esta interfaz si elige.  
  
## Notas para los llamadores  
 El SDM llama [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProgram2` para obtener esta interfaz para seguir las sesiones que han asociado a los programas.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProgramEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Asocia un programa una sesión.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado con un programa.|  
  
## Comentarios  
 esta interfaz es privada entre el SDM y el programa.  
  
## Requisitos  
 encabezado: Portpriv.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)