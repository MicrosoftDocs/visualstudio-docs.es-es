---
title: "IDebugEngine2::SetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetException"
helpviewer_keywords: 
  - "IDebugEngine2::SetException"
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica cómo el motor de depuración \(DE\) debe controlar una excepción especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Parámetros  
 `pException`  
 \[in\]  Una estructura de [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) que describe la excepción y cómo depurarlo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un OF podría indicar para detener el programa la generación de una excepción en la primera oportunidad, segunda oportunidad, o en absoluto.  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)