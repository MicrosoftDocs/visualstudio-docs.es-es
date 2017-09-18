---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType (método)"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método recupera la excepción asociada con un objeto, si existe.  
  
## Sintaxis  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### Parámetros  
 `ppException`  
 \[out\]  devuelve el objeto que representa la excepción.  
  
 `ppField`  
 \[out\]  Devuelve el objeto que representa un campo concreto que puede haber provocado la excepción \(puede ser un valor NULL\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
> [!NOTE]
>  Para comprobar si hay una excepción, compruebe el valor devuelto por `ppException`: si un valor es null, no existe ninguna excepción asociado a este objeto.  
  
## Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)