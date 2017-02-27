---
title: "IDebugExceptionEvent2::GetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::GetException"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::GetException"
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene una descripción detallada de la excepción que desencadenó este evento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```c#  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### Parámetros  
 `pExceptionInfo`  
 \[in, out\]  Una estructura de [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) se completa con la descripción de la excepción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 \[C\+\+ sólo\] el autor de llamada se es responsable de liberar cualquier cadena en la estructura de [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) así como lanzar el objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) en la estructura.  
  
## Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)