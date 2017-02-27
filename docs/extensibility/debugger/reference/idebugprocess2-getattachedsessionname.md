---
title: "IDebugProcess2::GetAttachedSessionName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
helpviewer_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene el nombre de la sesión que está depurando este proceso.  El IDE puede mostrar esta información a un usuario que está depurando un proceso determinado en un equipo determinado.  
  
> [!NOTE]
>  Se deja de utilizar este método, y la implementación debe devolver siempre `E_NOTIMPL`.  
  
## Sintaxis  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### Parámetros  
 `pbstrSessionName`  
  
## Valor devuelto  
 este método debe devolver siempre `E_NOTIMPL`.  
  
## Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)