---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
Agrega un scriptlet de código como elemento secundario del objeto de `IScriptNode` de nivel raíz.  En el host, el nombre completo del scriptlet se permite tener sólo dos niveles.  
  
## Sintaxis  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parámetros  
 `pszDefaultName`  
 \[in\] dirección del nombre predeterminado para asociar al scriptlet.  
  
 `pszCode`  
 \[in\] dirección del texto de scriptlet.  
  
 `pszItemName`  
 \[in\] dirección de búfer del identificador de nivel superior del nombre completo del scriptlet en el host.  
  
 `pszSubItemName`  
 \[in\] dirección de búfer del identificador del segundo nivel de nombre completo del scriptlet en el host.  Establezca en NULL si el nombre tiene un solo nivel.  
  
 `pszEventName`  
 \[in\] dirección de un búfer que contiene el nombre de evento para el que el scriptlet es un controlador de eventos.  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\-script\- bloque.  Cuando `pszCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final del bloque de script.  Establezca este parámetro en NULL si un delimitador no marca el final del bloque de script.  
  
 `dwCookie`  
 \[in\] valor definido por la aplicación que se usa para asociar el scriptlet con un objeto host.  
  
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