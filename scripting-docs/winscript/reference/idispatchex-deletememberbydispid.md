---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DeleteMemberByDispID (método)"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
Elimina un miembro por DISPID.  
  
## Sintaxis  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### Parámetros  
 `id`  
 Identificador de miembro.  Aplicaciones `GetDispID` o `GetNextDispID` de obtener el identificador de envío.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|El miembro existe pero no se puede eliminar.|  
  
## Comentarios  
 Si elimina el miembro, el DISPID debe seguir siendo válido para `GetNextDispID`.  
  
 Si elimina un miembro con un nombre determinado y crear después un miembro con el mismo nombre, el identificador de envío debe ser el mismo.  \(Si los nombres de miembro que sólo difieren en el caso son “igual” es dependiente objeto.\)  
  
## Ejemplo  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)