---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID (método)"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
Asigna un único nombre de miembro al DISPID correspondiente, que se puede utilizar en llamadas subsiguientes a `IDispatchEx::InvokeEx`.  
  
## Sintaxis  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### Parámetros  
 `bstrName`  
 Pasado en el nombre que se va a asignar.  
  
 `grfdex`  
 Determina las opciones para obtener el identificador de miembro.  Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|fdexNameCaseSensitive|Las solicitudes esas la búsqueda de nombre se hace de manera distingue entre mayúsculas y minúsculas.  Puede omitir por el objeto que no admite búsqueda distingue entre mayúsculas y minúsculas.|  
|fdexNameEnsure|Solicitudes que facilitan el miembro si no existen ya.  El nuevo miembro se debe crear con el valor `VT_EMPTY`.|  
|fdexNameImplicit|Indica que el llamador busca los objetos para un miembro de un nombre determinado cuando el objeto base no se especifica.|  
|fdexNameCaseInsensitive|Las solicitudes esas la búsqueda de nombre se hace de manera sin distinción entre mayúsculas y minúsculas.  Puede omitir por el objeto que no admite búsqueda sin distinción entre mayúsculas y minúsculas.|  
  
 `pid`  
 Puntero a la ubicación asignados por el llamador reciba resultado de DISPID.  Si se produce un error, `pid` contiene DISPID\_UNKNOWN.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`E_OUTOFMEMORY`|Memoria insuficiente.|  
|`DISP_E_UNKNOWNNAME`|El nombre no es conocido.|  
  
## Comentarios  
 `GetDispID` se puede utilizar en lugar de `GetIDsOfNames` para obtener el identificador de envío de un miembro determinado.  
  
 Dado que `IDispatchEx` permite la adición y eliminación de miembros, el conjunto de identificadores dispid no permanece constante para la duración de un objeto.  
  
 El parámetro no de `riid` en `IDispatch::GetIDsOfNames` se ha quitado.  
  
## Ejemplo  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)