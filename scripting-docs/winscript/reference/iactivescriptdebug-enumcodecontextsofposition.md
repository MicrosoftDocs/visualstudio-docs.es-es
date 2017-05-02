---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
Utilizado por un host inteligente para delegar el método de `IDebugDocumentContext::EnumCodeContexts`.  
  
## Sintaxis  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parámetros  
 `dwSourceContext`  
 \[in\] contexto de origen de El que se indica a `IActiveScriptParse::ParseScriptText` o a `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] inicio en relación con offset del carácter del texto del script.  
  
 `uNumChars`  
 \[in\] número de caracteres en este contexto.  
  
 `ppescc`  
 \[out\] un enumerador de los contextos de código en el rango especificado.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Hospeda inteligentes utilizan este método para delegar el método de `IDebugDocumentContext::EnumCodeContexts` .  
  
## Vea también  
 [IActiveScriptDebug \(Interfaz\)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)