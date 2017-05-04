---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
Devuelve información del lenguaje.  
  
## Sintaxis  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### Parámetros  
 `pgrfasa`  
 \[out\] marcas de El que contienen la información del lenguaje.  Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|El lenguaje prefiere la creación del controlador de eventos de script por el motor de creación de script en lugar de la aplicación.|  
|fasaSupportInternalHandler|0x0002|Los controladores de eventos de script de las compatibilidad con idiomas creados por el motor de creación de script.|  
|fasaCaseSensitive|0x0004|El lenguaje de comandos distinguen entre mayúsculas y minúsculas.|  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Si el motor de creación de script administra controladores de eventos, la aplicación debe llamar a `CreateChildHandler` de un objeto de `IScriptEntry` .  Esto crea un objeto de `IScriptScriptlet` que corresponde al controlador de eventos.  El motor también agrega un controlador de eventos a la entrada del script.  El controlador de eventos es una función vacía que contiene la información especificada de la signatura.  
  
 Si la aplicación administra controladores de eventos, debe llamar a `CreateChildHandler` de un objeto de `IScriptNode` que representa un scriptlet del controlador de eventos.  Esto crea un objeto de `IScriptScriptlet` asociado al scriptlet del controlador de eventos.  La aplicación también tiene que agregar una función vacía como controlador de eventos a un nuevo o existente objeto de `IScriptEntry` .  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)