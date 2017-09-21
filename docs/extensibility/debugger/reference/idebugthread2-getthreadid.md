---
title: "IDebugThread2::GetThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetThreadId"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadId"
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el identificador de subproceso del sistema.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```c#  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### Parámetros  
 `pdwThreadId`  
 \[out\]  Devuelve el identificador del subproceso del sistema.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un identificador de subproceso se utiliza para identificar el subproceso entre el resto de los subprocesos de un proceso.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CProgram` que implemente la interfaz de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)