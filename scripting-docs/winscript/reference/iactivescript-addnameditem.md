---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem (método), IActiveScript (interfaz)"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
Agrega el nombre de un elemento de nivel raíz al espacio de nombres del motor de script.  Un elemento de nivel de raíz es un objeto con propiedades y métodos, un origen de eventos, o los tres.  
  
## Sintaxis  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### Parámetros  
 `pstrName`  
 \[in\] dirección de un búfer que contiene el nombre del elemento presentada de script.  El nombre debe ser único y con persistencia.  
  
 `dwFlags`  
 \[in\] marcas asociadas a un elemento.  Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTITEM\_CODEONLY|Indica que el elemento denominado representa un objeto de código \- únicamente, y que el host no tiene ningún `IUnknown` esté asociada a este objeto de código \- únicamente.  El host tiene sólo un nombre para este objeto.  En lenguajes orientados a objetos como C\+\+, este marcador crearía una clase.  No todos los lenguajes admiten este marcador.|  
|SCRIPTITEM\_GLOBALMEMBERS|Indica que el elemento es una colección de propiedades globales y métodos asociados al script.  Normalmente, un motor de scripting omitiría el nombre de objeto \(distinto con el fin de utilizarla como una cookie para el método de [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) , o resolver ámbito explícito\) y expondría sus miembros como variables globales y métodos.  Esto permite al host extiende la biblioteca \(funciones en tiempo de ejecución etc.\) disponibles para el script.  Se permite al motor de script para solucionar conflictos de nombre \(por ejemplo, si dos elementos de SCRIPTITEM\_GLOBALMEMBERS tienen métodos del mismo nombre\), aunque el error no se debe devolver debido a esta situación.|  
|SCRIPTITEM\_ISPERSISTENT|Indica que el elemento debe guardarse si se guarda el motor de script.  De igual forma, establecer este marcador indica que una transición al estado inicializado debe conservar el nombre del elemento y la información de tipo \(el motor de script debe, sin embargo, liberar todos los punteros a interfaces del objeto real\).|  
|SCRIPTITEM\_ISSOURCE|Indica que los eventos de los orígenes del elemento que el script puede recibir.  Los objetos secundarios \(propiedades de objeto que en ellos mismos objetos\) también pueden los eventos del origen al script.  Esto no es recursiva, pero proporciona un mecanismo apropiado para el caso común, por ejemplo, para crear un contenedor y todos sus controles de miembro.|  
|SCRIPTITEM\_ISVISIBLE|Indica que el nombre del elemento está disponible en el espacio de nombres de script, que permite el acceso a las propiedades, métodos, y eventos del elemento.  Por convención las propiedades los elementos secundarios de inclusión del elemento; por consiguiente, todas las propiedades de objeto secundario y métodos \(y sus elementos secundarios, de forma recursiva\) estarán disponibles.|  
|SCRIPTITEM\_NOCODE|Indica que el elemento es simplemente un nombre que se agrega al espacio de nombres del script, y no se deben tratar como un elemento para el que el código debe estar asociado.  Por ejemplo, sin este marcador que se establece, VBScript creará un módulo independiente para el elemento especificado, y C\+\+ podría crear una clase contenedora independiente para el elemento especificado.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)