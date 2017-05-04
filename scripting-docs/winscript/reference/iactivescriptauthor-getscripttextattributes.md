---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de script.  
  
## Sintaxis  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### Parámetros  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] El texto del bloque de script.  Esta cadena no tiene que ser NULL cancelada.  
  
 `cch`  
 \[in\] tamaño de El utilizado para los parámetros de `pszCode` y de `pattr` .  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\- script.  Cuando `pszCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final de scriptlet.  Establezca este parámetro en NULL si no hay delimitador para identificar el final del bloque de script.  
  
 `dwFlags`  
 \[in\] marcas de El que se asocian a los atributos de texto del bloque de script.  Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identifique los identificadores que tienen el atributo de SOURCETEXT\_ATTR\_IDENTIFIER, e identificar los operadores de puntos que tienen el atributo de SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Identifica el objeto actual que tiene el atributo de SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Identifica el contenido y el texto del comentario de la cadena que tiene el atributo de SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is \(`cch`\)\] La información de color para el código de bloque de script.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)