---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
Utilizado por el motor del lenguaje para delegar `IDebugCodeContext::GetSourceContext`.  
  
## Sintaxis  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parámetros  
 `dwSourceContext`  
 \[in\] contenido de origen de El que se indica a `ParseScriptText` o a `AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] inicio en relación con offset del carácter de bloque o de scriptlet de script.  
  
 `uNumChars`  
 \[in\] número de caracteres en este contexto.  
  
 `ppsc`  
 \[out\] contexto de documento de El correspondiente a este intervalo de la posición.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Los motores de lenguaje utilizan este método para delegar `IDebugCodeContext::GetSourceContext`.  
  
## Vea también  
 [IActiveScriptSiteDebug \(Interfaz\)](../../winscript/reference/iactivescriptsitedebug-interface.md)