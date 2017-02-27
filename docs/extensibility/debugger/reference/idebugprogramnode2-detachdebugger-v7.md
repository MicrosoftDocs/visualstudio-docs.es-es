---
title: "IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::DetachDebugger"
helpviewer_keywords: 
  - "IDebugProgramNode2::DetachDebugger"
  - "IDebugProgramNode2::DetachDebugger_V7"
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

DESUSADO.  NOT UTILICE.  
  
## Sintaxis  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## Valor devuelto  
 Una implementación siempre debe devolver `E_NOTIMPL`.  
  
## Comentarios  
  
> [!WARNING]
>  A partir de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], este método se utiliza y debe ya no devolver siempre `E_NOTIMPL`.  
  
 Se llama a este método cuando el depurador finaliza inesperadamente.  Cuando se llama a este método, el OF debe reanudar el programa como si el usuario desasociado de.  No más eventos de depuración deben ser enviados.  El programa debe estar en un estado donde conectable de otra instancia del depurador.  
  
## Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)