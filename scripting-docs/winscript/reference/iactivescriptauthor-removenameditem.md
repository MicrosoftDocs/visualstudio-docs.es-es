---
title: "IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveNamedItem"
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::RemoveNamedItem
Quita un objeto de `NamedItem` del motor de creación de script.  
  
## Sintaxis  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### Parámetros  
 `pszName`  
 \[in\] dirección del búfer que identifica el objeto de `NamedItem` para quitar.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`S_FALSE`|El objeto de `NamedItem` no está presente en el espacio de nombres del motor de creación de script.|  
  
## Comentarios  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) se utiliza para insertar el objeto de `NamedItem` en el espacio de nombres del script del motor de creación.  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)