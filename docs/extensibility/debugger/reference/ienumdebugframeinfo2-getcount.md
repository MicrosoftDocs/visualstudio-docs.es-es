---
title: "IEnumDebugFrameInfo2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2::GetCount"
ms.assetid: d02a08e3-f34f-461e-8195-5157e154c481
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugFrameInfo2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

devuelve el número de elementos en la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### Parámetros  
 `pcelt`  
 \[out\]  devuelve el número de elementos en la enumeración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método no forma parte de la interfaz COM habitual de enumeración que especifica que sólo `Next`, `Clone`, `Skip`, y los métodos de `Reset` necesitan implementarse.  
  
## Vea también  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)