---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNextDispID (método)"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
Enumera los miembros del objeto.  
  
## Sintaxis  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### Parámetros  
 `grfdex`  
 Determina que establece de elementos debe ser enumerada.  Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|fdexEnumDefault|Solicitudes que el objeto enumera los elementos predeterminados.  El objeto puede mostrar cualquier conjunto de elementos.|  
|fdexEnumAll|Solicitudes que el objeto muestra todos los elementos.  El objeto puede mostrar cualquier conjunto de elementos.|  
  
 `id`  
 Identifica el miembro actual.  GetNextDispID recupera el elemento de la enumeración a ésta.  Aplicaciones GetDispID o una llamada anterior a GetNextDispID de obtener este identificador.  Utiliza el valor de DISPID\_STARTENUM para obtener el primer identificador del primer elemento.  
  
 `pid`  
 Dirección de una variable de DISPID que recibe el identificador del siguiente elemento de la enumeración.  
  
 Si `DeleteMemberByDispID`elimina un miembro `DeleteMemberByName` o, las necesidades de `DISPID` de seguir siendo válido para `GetNextDispID`.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|Se realiza la enumeración.|  
  
## Ejemplo  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)