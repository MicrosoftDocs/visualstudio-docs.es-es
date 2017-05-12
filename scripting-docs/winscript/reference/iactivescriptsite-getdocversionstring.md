---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
Recupera una cadena host\- definido que identifica de forma única la versión del documento actual.  Si el documento relacionado ha cambiado fuera del ámbito de script de Windows \(como en el caso de una página HTML que se está editando con el Bloc de notas\), el motor de script puede guardar esto junto con su estado almacenado, forzar una recompilación la próxima vez que el script se carga.  
  
## Sintaxis  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### Parámetros  
 `pstrVersionString`  
 \[out\] dirección de la cadena host\- definido de la versión del documento.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_NOTIMPL` si este método no se admite.  
  
## Comentarios  
 Si se devuelve `E_NOTIMPL` , el motor de script debe suponer que el script está en sincronización con el documento.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)