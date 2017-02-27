---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene una representación equipo\-dependiente de intervalo de direcciones físicas asociado a un marco de pila.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### Parámetros  
 `paddrMin`  
 \[out\]  Devuelve la dirección física inferior asociado a este marco de pila.  
  
 `paddrMax`  
 \[out\]  Devuelve la dirección física más alta asociado a este marco de pila.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La información devuelta por este método utiliza el administrador de depuración de la sesión \(SDM\) para ordenar los marcos de pila.  
  
 Se supone que la pila de llamadas crece siguiente, es decir, que los nuevos marcos de pila se agregan en direcciones de memoria cada vez más bajo.  Una arquitectura de runtime debe proporcionar intervalos físicos de pila que coinciden con esta suposición.  
  
## Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)