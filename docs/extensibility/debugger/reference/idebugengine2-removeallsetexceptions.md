---
title: "IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveAllSetExceptions"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveAllSetExceptions"
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Quita la lista de excepciones que el IDE ha establecido para una arquitectura o un lenguaje específica del motor en tiempo de ejecución.  
  
## Sintaxis  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```c#  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### Parámetros  
 `guidType`  
 \[in\]  GUID para el idioma o el GUID del motor de depuración que es específico de una arquitectura en tiempo de ejecución.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las excepciones quitadas con este método se establecen mediante llamadas anteriores al método de [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .  
  
 Para quitar una excepción concreta, llame al método de [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)