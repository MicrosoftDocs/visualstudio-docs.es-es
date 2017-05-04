---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
Devuelve el scriptlet que tiene los atributos especificados.  
  
## Sintaxis  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parámetros  
 `pdisp`  
 \[in\] objeto de El `IDispatch` que corresponde a `NamedItem` a las que se asocia el scriptlet.  
  
 `pszItem`  
 \[in\] dirección de búfer del identificador de nivel superior del nombre completo del scriptlet en el host.  
  
 `pszSubItem`  
 \[in\] dirección de búfer del identificador del segundo nivel de nombre completo del scriptlet en el host.  Establezca en NULL si el nombre tiene un solo nivel.  
  
 `pszEvent`  
 \[in\] dirección de un búfer que contiene el nombre del evento.  El scriptlet es un controlador para este evento.  
  
 `ppse`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de `IScriptEntry` de scriptlet que tiene los atributos especificados.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)