---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
Agrega el nombre de un elemento de nivel raíz al espacio de nombres del script del motor de creación.  *Un elemento de nivel de raíz* es un objeto que pueden contener propiedades y métodos, y que puede contener también un origen de eventos.  
  
## Sintaxis  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### Parámetros  
 `pszName`  
 \[in\] nombre del elemento presentada de script.  El nombre debe ser único y con persistencia.  
  
 `dwFlags`  
 \[in\] marcas de El que se asocia el elemento denominado.  Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|Indica que el nombre del elemento está disponible en el espacio de nombres del script.  Esto permite el acceso a las propiedades, métodos, y eventos del elemento.<br /><br /> Por convención, las propiedades del elemento incluyen los miembros secundarios del elemento.  Por consiguiente, todas las propiedades de objeto secundario y métodos \(y sus miembros secundarios, de forma recursiva\) son accesibles.|  
|SCRIPTITEM\_ISSOURCE|0x00000004|Indica los eventos del origen del elemento que el script puede tener controladores de eventos del script.|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|Indica que el elemento es una colección de propiedades globales y los métodos asociados al script.  Crean sus miembros como variables globales y métodos.|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|Indica que el elemento debe guardarse si se guarda el motor de creación de script.|  
|SCRIPTITEM\_CODEONLY|0x00000200|Indica que el elemento denominado representa un objeto de código \- únicamente, y no tiene un miembro a crear.|  
|SCRIPTITEM\_NOCODE|0x00000400|Indica que el elemento denominado es simplemente un nombre incluido, y no tiene nada crear.|  
  
 `pdisp`  
 \[in\] `IDispatch` del objeto de `NamedItem` que se utiliza para recopilar métodos, propiedades, o el origen de eventos.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)