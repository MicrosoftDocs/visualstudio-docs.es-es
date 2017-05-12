---
title: "IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptTextAttributes"
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque arbitrario de texto del script.  
  
## Sintaxis  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parámetros  
 `pstrCode`  
 \[in\] texto de bloque de script de El.  Esta cadena no necesita ser NULL cancelada.  
  
 `uNumCodeChars`  
 \[in\] número de caracteres del texto de bloque de script.  
  
 `pstrDelimiter`  
 \[in\] dirección de delimitador de FIN\-de\-script\- bloque.  Cuando `pstrCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas simples \('\), para detectar el final del bloque de script.  Este parámetro especifica el delimitador que el host utilizado, permitiendo que el motor de script proporcione algún preprocesamiento primitivo condicional \(por ejemplo, reemplazando una comilla simple \['\] con dos comillas sencillas para el uso como delimitador\).  Exactamente cómo \(y si\) el motor de script utiliza esta información depende del motor de script.  Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 \[in\] marcas asociadas al bloque de script.  Puede ser una combinación de estos valores:  
  
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
  
 Este método para los bloques de script; el método de `GetScriptletTextAttributes` es para los scriptletes.  
  
## Vea también  
 [IActiveScriptDebug \(Interfaz\)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)