---
title: "IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetScriptTextAttributes"
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de texto del documento.  
  
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
|`E_NOTIMPL`|El host utiliza sólo atributos predeterminados.|  
  
## Comentarios  
 Este método devuelve los atributos de texto de un bloque de texto del documento arbitrario.  Es aceptable que hospeda devuelven `E_NOTIMPL`, en cuyo caso se utilizan atributos predeterminados.  
  
## Vea también  
 [IDebugDocumentHost \(Interfaz\)](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)