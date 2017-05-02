---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
Permite que el motor de script obtiene información sobre un elemento agregado con el método de [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## Sintaxis  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### Parámetros  
 `pstrName`  
 \[in\] nombre de El asociado al elemento, como se especifica en el método de [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 \[in\] la especificación de una máscara de bits de qué información sobre el elemento debe ser devuelta.  El motor de script debe solicitar la mínima cantidad de información posible porque algunos de los parámetros devueltos \(por ejemplo, `ITypeInfo`\) pueden tardar considerable tiempo para cargar o generar.  Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTINFO\_IUNKNOWN|Devuelve la interfaz de `IUnknown` para este elemento.|  
|SCRIPTINFO\_ITYPEINFO|Devuelve la interfaz de `ITypeInfo` para este elemento.|  
  
 `ppunkItem`  
 \[out\] la dirección de una variable que recibe un puntero a la interfaz de `IUnknown` asociado al elemento especificado.  El motor de script puede utilizar el método de `IUnknown::QueryInterface` para obtener la interfaz de `IDispatch` para el elemento.  Este parámetro recibe NULL si `dwReturnMask` no incluye el valor de SCRIPTINFO\_IUNKNOWN.  También, recibe NULL si no hay ningún objeto asociado al nombre de elemento; este mecanismo se utiliza para crear una clase simple cuando el elemento denominado se agregó al conjunto marca SCRIPTITEM\_CODEONLY en el método de [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 \[out\] la dirección de una variable que recibe un puntero a la interfaz de `ITypeInfo` asociado al elemento.  Este parámetro recibe NULL si `dwReturnMask` no incluye el valor de SCRIPTINFO\_ITYPEINFO, o si la información de tipo no está disponible para este elemento.  Si la información de tipo no está disponible, el objeto no puede los eventos del origen, y el enlace de nombre se deben observar con el método de `IDispatch::GetIDsOfNames` .  Observe que la interfaz de `ITypeInfo` recuperada describe la coclase de elementos \(TKIND\_COCLASS\) porque el objeto puede admitir varias interfaces y las interfaces de eventos.  Si el elemento admite la interfaz de `IProvideMultipleTypeInfo` , la interfaz de `ITypeInfo` recuperada es igual que el índice cero `ITypeInfo` que se recopilaron mediante el método de `IProvideMultipleTypeInfo::GetInfoOfIndex` .  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un elemento name especificado no se encuentra.|  
  
## Comentarios  
 Este método recupera sólo la información indicada por el parámetro de `dwReturnMask` ; esto mejora el rendimiento.  Por ejemplo, si una interfaz de `ITypeInfo` no es necesaria para un elemento, no se especifica simplemente en `dwReturnMask`.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)