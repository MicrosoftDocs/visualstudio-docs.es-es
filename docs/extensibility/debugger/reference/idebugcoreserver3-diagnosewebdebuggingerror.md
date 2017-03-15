---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::DiagnoseWebDebuggingError"
helpviewer_keywords: 
  - "IDebugCoreServer3::DiagnoseWebDebuggingError"
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Intentos de determinar la causa del error de una asociación automática.  
  
## Sintaxis  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### Parámetros  
 `pszUrl`  
 \[in\]  No se usa actualmente; debe establecerse siempre en un valor nulo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Los siguientes son los códigos devueltos típicos:  
  
|Código|Descripción|  
|------------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|No puede determinar por qué el servidor remoto no podría para iniciar la depuración.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|No puede depurar en el servidor remoto, posiblemente debido a permisos insuficientes o porque el verbo DEBUG no está habilitada.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|El servidor web ha bloqueado y está bloqueando el verbo DEBUG, necesario para habilitar la depuración.|  
  
## Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)