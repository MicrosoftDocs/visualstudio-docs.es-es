---
title: "IDebugExpressionContext::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext.GetLanguageInfo
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext::GetLanguageInfo"
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext::GetLanguageInfo
Devuelve un nombre y GUID del lenguaje que posee este contexto.  
  
## Sintaxis  
  
```  
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### Parámetros  
 `pbstrLanguageName`  
 \[out\] nombre del lenguaje.  
  
 `pLanguageID`  
 \[out\] id. único para obtener el lenguaje.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve un nombre y GUID del lenguaje que posee este contexto.  
  
## Vea también  
 [IDebugExpressionContext \(Interfaz\)](../../winscript/reference/idebugexpressioncontext-interface.md)