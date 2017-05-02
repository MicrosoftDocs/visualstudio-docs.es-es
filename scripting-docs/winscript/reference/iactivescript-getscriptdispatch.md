---
title: "IActiveScript::GetScriptDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptDispatch"
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptDispatch
Recupera la interfaz de `IDispatch` para los métodos y propiedades asociados al script que se está ejecutando actualmente.  
  
## Sintaxis  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### Parámetros  
 `pstrItemName`  
 \[in\] dirección de un búfer que contiene el nombre del elemento para el que el llamador necesita el objeto asociado de envío.  Si este parámetro es `NULL`, el objeto de envío contiene como miembros todos los métodos globales y las propiedades definidas por el script.  A través de la interfaz de `IDispatch` y la interfaz asociada de `ITypeInfo` , el host puede invocar métodos o la vista de script y modificar las variables de script.  
  
 `ppdisp`  
 \[out\] la dirección de una variable que recibe un puntero al objeto asociado a los métodos globales y propiedades del script.  Si el motor de script no admite este tipo de objeto, se devuelve `NULL` .  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
|`S_FALSE`|El motor de script no admite un objeto de envío; el parámetro de `ppdisp` se establece en NULL.|  
  
## Comentarios  
 Dado que los métodos y propiedades que se pueden agregar llamando a la interfaz de [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , la interfaz de `IDispatch` devuelta por este método puede admitir dinámicamente nuevos métodos y propiedades.  De igual forma, el método de `IDispatch::GetTypeInfo` debe devolver una nueva, única interfaz de `ITypeInfo` cuando se agregan los métodos y propiedades.  Observe, sin embargo, que los motores de lenguaje no deben cambiar la interfaz de `IDispatch` de manera que sea incompatible con cualquier interfaz anterior de `ITypeInfo` devuelta.  Esto implica, por ejemplo, que los identificadores dispid nunca se reutilizarla.  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)