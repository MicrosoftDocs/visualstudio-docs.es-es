---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
El texto del script de los análisis, se agrega texto al motor de creación de script, y crea un objeto de `IScriptEntry` que corresponde al bloque de script.  
  
## Sintaxis  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parámetros  
 `pszCode`  
 \[in\] texto del script de Va a analizar.  
  
 `pszItemName`  
 \[in\] dirección del búfer a El que contiene el nombre del elemento asociado al bloque de script.  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\-script\- bloque.  Cuando `pszCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final del bloque de script.  Establezca este parámetro en NULL si no hay delimitador para identificar el final del bloque de script.  
  
 `dwCookie`  
 \[in\] valor definido por la aplicación asociada al nuevo objeto de `IScriptEntry` .  
  
 `dwFlags`  
 \[in\] No se utiliza.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)