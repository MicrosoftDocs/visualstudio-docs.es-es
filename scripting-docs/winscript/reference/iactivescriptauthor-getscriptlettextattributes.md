---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptletTextAttributes"
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::GetScriptletTextAttributes
Devuelve los atributos de texto de un scriptlet.  
  
## Sintaxis  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### Parámetros  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] El texto de scriptlet.  Esta cadena no tiene que ser NULL cancelada.  
  
 `cch`  
 \[in\] tamaño de El utilizado para los parámetros de `pszCode` y de `pattr` .  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\- scriptlet.  Cuando `pszCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final de scriptlet.  Establezca este parámetro en NULL si no se usa ningún delimitador para identificar el final de scriptlet.  
  
 `dwFlags`  
 \[in\] marcas de El que se asocian a los atributos de texto de scriptlet.  Puede ser una combinación de los siguientes valores.  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identifique los identificadores que tienen el atributo de SOURCETEXT\_ATTR\_IDENTIFIER, e identificar los operadores de puntos que tienen el atributo de SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Identifica el objeto actual que tiene el atributo de SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Identifica el contenido y el texto del comentario de la cadena que tiene el atributo de SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is \(`cch`\)\] La información de color para el código de scriptlet.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE\_TEXT\_ATTR \(Enumeración\)](../../winscript/reference/source-text-attr-enumeration.md)