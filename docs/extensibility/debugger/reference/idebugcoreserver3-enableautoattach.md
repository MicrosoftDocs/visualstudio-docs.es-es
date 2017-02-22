---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite asociar automático para los motores especificados de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### Parámetros  
 `rgguidSpecificEngines`  
 \[in\]  Matriz de GUID para que cada motor de depuración marcado como auto\-adjuntando.  
  
 `celtSpecificEngines`  
 \[in\]  el número de motores especificados en `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 \[in\]  La dirección URL que empieza a utilizar el auto\-adjuntar.  
  
 `pbstrSessionID`  
 \[out\]  Identificador de la sesión que auto\-fue asociada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Un código de error es `E_AUTO_ATTACH_NOT_REGISTERED`, que indica que el generador de la clase de la asociación automática no se ha registrado.  
  
## Comentarios  
 Cuando un programa asociado con la dirección URL especificada se inicia, los motores especificados de depuración se inician y se adjuntan.  
  
## Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)