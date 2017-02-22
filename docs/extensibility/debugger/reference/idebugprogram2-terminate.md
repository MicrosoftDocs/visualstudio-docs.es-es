---
title: "IDebugProgram2::Terminate | Microsoft Docs"
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
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

finaliza el programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si es posible, el programa terminará y descargar del proceso; si no, el motor de depuración \(DE\) funcionará cualquier limpieza necesaria.  
  
 Este método o el método de [Terminar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) llama el IDE, normalmente en respuesta al usuario que detiene toda la depuración.  La implementación de este método debe, finalizar idealmente el programa dentro del proceso.  Si no es posible, el OF debe evitar que el programa se ejecute más en este proceso \(y realizar cualquier limpieza necesaria\).  Si el método de `IDebugProcess2::Terminate` se llama el IDE, el proceso terminará en algún momento después de que se llame al método de `IDebugProgram2::Terminate` .  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)