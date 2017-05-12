---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByName (método)"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
Elimina un miembro por nombre.  
  
## Sintaxis  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### Parámetros  
 `bstrName`  
 Nombre del miembro que se va a eliminar.  
  
 `grfdex`  
 Determina si el nombre de miembro distingue entre mayúsculas y minúsculas.  Puede ser cualquiera de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|fdexNameCaseSensitive|Las solicitudes esas la búsqueda de nombre se hace de manera distingue entre mayúsculas y minúsculas.  Puede omitir por el objeto que no admite búsqueda distingue entre mayúsculas y minúsculas.|  
|fdexNameCaseInsensitive|Las solicitudes esas la búsqueda de nombre se hace de manera sin distinción entre mayúsculas y minúsculas.  Puede omitir por el objeto que no admite búsqueda sin distinción entre mayúsculas y minúsculas.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|El miembro existe pero no se puede eliminar.|  
  
## Comentarios  
 Si elimina el miembro, el DISPID debe seguir siendo válido para `GetNextDispID`.  
  
 Si elimina un miembro con un nombre determinado y crear después un miembro con el mismo nombre, el identificador de envío debe ser el mismo.  \(Si los miembros que sólo difieren en el caso son “igual” es dependiente objeto.\)  
  
## Ejemplo  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)