---
title: "IEnumDebugThreads2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugThreads2::GetCount"
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugThreads2::GetCount
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
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)