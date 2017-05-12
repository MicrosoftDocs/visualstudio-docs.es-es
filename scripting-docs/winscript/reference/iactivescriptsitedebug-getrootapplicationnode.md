---
title: "IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetRootApplicationNode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetRootApplicationNode"
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetRootApplicationNode
Obtiene el nodo de la aplicación en el que los documentos de script deben agregarse.  
  
## Sintaxis  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Parámetros  
 `ppdanRoot`  
 \[out\] nodo de aplicación de depuración a El que contiene documentos de script.  Puede ser `NULL`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el nodo de la aplicación en el que los documentos de script deben agregarse.  El método puede devolver `NULL` para `ppdanRoot` si los documentos de script son de nivel superior.  
  
## Vea también  
 [IActiveScriptSiteDebug \(Interfaz\)](../../winscript/reference/iactivescriptsitedebug-interface.md)