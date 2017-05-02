---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
Clona el motor de scripting actual \(menos cualquier estado de ejecución actual\), y devuelve un motor carga de script que no tiene ningún sitio en el subproceso actual.  Las propiedades de este nuevo motor de scripting se idénticas a las propiedades que el motor de script original sería en si cambiar de nuevo al estado inicializado.  
  
## Sintaxis  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### Parámetros  
 `ppscript`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de [IActiveScript](../../winscript/reference/iactivescript.md) de motor clonado de script.  El host debe crear un sitio y llamar al método de [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) en el nuevo motor de script antes de que esté en el estado inicializado y, por consiguiente, utilizable.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|Este método no es compatible.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
  
## Comentarios  
 El método de `IActiveScript::Clone` es una optimización de `IPersist*::Save`, de `CoCreateInstance`, y de `IPersist*::Load`, por lo que el estado de nuevo motor de scripting debe ser el mismo que si se guardaran y se carga el estado del motor de script original en nuevo script un motor.  Los elementos con nombre se duplican en el motor clonado de script, pero los punteros específicos del objeto para cada elemento se olvidan y se recopilan con el método de [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) .  Esto permite que un modelo de objetos idéntico a puntos de entrada de por\- subproceso \(un modelo apartamento\) utiliza.  
  
 Este método se utiliza para los hosts multiproceso de servidor que pueden ejecutar varias instancias del mismo script.  El motor de script puede devolver `E_NOTIMPL`, en cuyo caso el host puede lograr el mismo resultado duplicando el estado persistente y crea una nueva instancia del motor de script con una interfaz de `IPersist*` .  
  
 Se puede llamar a este método de los subprocesos de la interfaz no base fuera lo que da como resultado una llamada no base para hospedar objetos o a la interfaz de [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)