---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
Devuelve los atributos de texto para un scriptlet arbitrario.  
  
## Sintaxis  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parámetros  
 `pstrCode`  
 \[in\] texto de scriptlet de El.  Esta cadena no necesita ser NULL cancelada.  
  
 `uNumCodeChars`  
 \[in\] número de caracteres del texto de scriptlet.  
  
 `pstrDelimiter`  
 \[in\] dirección de delimitador de FIN\-de\- scriptlet.  Cuando `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final de scriptlet.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el fin de scriptlet.  
  
 `dwFlags`  
 \[in\] marcas asociados al scriptlet.  Puede ser una combinación de estos valores:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Indica que los identificadores y los operadores de punto deben identificarse con el SOURCETEXT\_ATTR\_IDENTIFIER y SOURCETEXT\_ATTR\_MEMBERLOOKUP marcadores, respectivamente.|  
|GETATTRFLAG\_THIS|0x0100|Indica que el identificador del objeto actual debe identificarse con el marcador de SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Indica que el contenido y el texto del comentario de la cadena deben identificar con el marcador de SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out\] búfer para contener los atributos devueltos.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un host inteligente que implementa la interfaz de `IDebugDocumentText` puede utilizar este método para delegar llamadas a métodos de `IDebugDocumentText::GetText` .  
  
 Se proporciona esta llamada porque los scriptletes tienden a ser expresiones y pueden tener una sintaxis diferente que un bloque de script.  Si tienen la misma sintaxis, la implementación de este método es idéntica a la implementación del método de `GetScriptTextAttributes` .  
  
## Vea también  
 [IActiveScriptDebug \(Interfaz\)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)