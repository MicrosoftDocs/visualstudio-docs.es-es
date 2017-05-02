---
title: "IDebugCookie::SetDebugCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugCookie::SetDebugCookie"
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCookie::SetDebugCookie
Establece la cookie de la aplicación de depuración.  
  
## Sintaxis  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### Parámetros  
 `dwDebugAppCookie`  
 \[in\] cookie de que identifica la aplicación de depuración.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método establece la cookie de la aplicación de depuración, que permite que más de un depurador se asocie a un proceso.  
  
## Vea también  
 [IDebugCookie \(Interfaz\)](../../winscript/reference/idebugcookie-interface.md)