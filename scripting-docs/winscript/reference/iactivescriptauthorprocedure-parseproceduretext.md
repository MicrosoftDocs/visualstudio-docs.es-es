---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
Analiza un procedimiento de código, agregue el texto del procedimiento de código al motor de creación de script, y crea un objeto de `IScriptEntry` correspondiente al procedimiento de código.  
  
## Sintaxis  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### Parámetros  
 `pszCode`  
 \[in\] texto del script de Va a analizar.  
  
 `pszFormalParams`  
 \[in\] dirección de los nombres de parámetros formales del procedimiento.  Los nombres de parámetro deben separarse por delimitadores adecuados para el motor de creación de script.  Los nombres no se deben agregar en paréntesis.  
  
 `pszProcedureName`  
 \[in\] dirección del nombre del procedimiento que se va a analizar.  
  
 `pszItemName`  
 \[in\] dirección del búfer a El que contiene el nombre del elemento asociado al objeto de `IScriptEntry` .  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\-script\- bloque.  Cuando `pszCode` se analiza de una secuencia de texto, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final del bloque de script.  Establezca este parámetro en NULL si no hay delimitador para marcar el final del bloque de script.  
  
 `dwCookie`  
 \[in\] valor definido por la aplicación asociada al nuevo objeto de `IScriptEntry` .  
  
 `dwFlags`  
 \[in\] No se utiliza.  
  
 `pdispFor`  
 \[in\] No se utiliza.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El motor actual de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no implementa este método.  
  
## Vea también  
 [IActiveScriptAuthorProcedure \(Interfaz\)](../../winscript/reference/iactivescriptauthorprocedure-interface.md)