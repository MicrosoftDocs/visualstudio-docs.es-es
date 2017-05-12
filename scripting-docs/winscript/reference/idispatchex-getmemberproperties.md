---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties (método)"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
Recupera las propiedades de miembro.  
  
## Sintaxis  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### Parámetros  
 `id`  
 Identifica el miembro.  Aplicaciones `GetDispID` o `GetNextDispID` de obtener el identificador de envío.  
  
 `grfdexFetch`  
 Determina qué propiedades se van a recuperar.  Puede ser una combinación de los valores enumerados en `pgrfdex` o una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|grfdexPropCanAll|Combina el fdexPropCanGet, el fdexPropCanPut, el fdexPropCanPutRef, el fdexPropCanCall, el fdexPropCanConstruct y fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina el fdexPropCannotGet, el fdexPropCannotPut, el fdexPropCannotPutRef, el fdexPropCannotCall, el fdexPropCannotConstruct y fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects y fdexPropDynamicType de las cosechadoras.|  
|grfdexPropAll|Combina el grfdexPropCanAll, el grfdexPropCannotAll y el grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Dirección de `DWORD` que recibe las propiedades solicitadas.  Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|fdexPropCanGet|El miembro se puede obtener mediante DISPATCH\_PROPERTYGET.|  
|fdexPropCannotGet|El miembro no se puede obtener mediante DISPATCH\_PROPERTYGET.|  
|fdexPropCanPut|El miembro se puede establecer con DISPATCH\_PROPERTYPUT.|  
|fdexPropCannotPut|El miembro no puede establecerse mediante DISPATCH\_PROPERTYPUT.|  
|fdexPropCanPutRef|El miembro se puede establecer con DISPATCH\_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|El miembro no puede establecerse mediante DISPATCH\_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|El miembro no tiene efectos secundarios.  Por ejemplo, un depurador podría con seguridad get\/set\/llamada este miembro sin cambiar el estado del script que se estaba depurando.|  
|fdexPropDynamicType|El miembro es dinámico y puede cambiar durante la duración del objeto.|  
|fdexPropCanCall|El miembro puede ser llamado como método mediante DISPATCH\_METHOD.|  
|fdexPropCannotCall|El miembro no se le llama como método mediante DISPATCH\_METHOD.|  
|fdexPropCanConstruct|El miembro puede ser llamado como constructor con DISPATCH\_CONSTRUCT.|  
|fdexPropCannotConstruct|El miembro no puede invocar como un constructor con DISPATCH\_CONSTRUCT.|  
|fdexPropCanSourceEvents|El miembro puede desencadenar eventos.|  
|fdexPropCannotSourceEvents|El miembro no puede desencadenar eventos.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`DISP_E_UNKNOWNNAME`|El nombre no es conocido.|  
  
## Ejemplo  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)