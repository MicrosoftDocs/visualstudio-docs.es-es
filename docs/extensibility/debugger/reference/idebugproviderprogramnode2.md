---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz forma interfaces relacionadas con el programa a través de límites de procesos.  
  
## Sintaxis  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir interfaces de cálculo de referencias entre los límites del proceso.  
  
## Notas para los llamadores  
 Llame a [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProgramNode2` para obtener esta interfaz.  Si esta interfaz no puede obtenerse, el OF no admite el cálculo de referencias de interfaces.  
  
## métodos en el orden de Vtable  
 esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtiene una interfaz especificada a través de límites de procesos.|  
  
## Comentarios  
 Se implementa esta interfaz cuando se ejecuta en un espacio de proceso independiente del programa que se depura: por ejemplo, cuando el OF se ejecuta en el espacio del proceso de Visual Studio en lugar del espacio de proceso del programa que se depura.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)