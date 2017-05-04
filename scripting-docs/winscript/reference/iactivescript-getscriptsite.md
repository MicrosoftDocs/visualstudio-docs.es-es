---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
Recupera el objeto de sitio asociado al motor de scripts de Windows.  
  
## Sintaxis  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### Parámetros  
 `iid`  
 \[in\] identificador de la interfaz solicitada.  
  
 `ppvSiteObject`  
 \[out\] dirección de la ubicación que recibe el puntero de interfaz al objeto de sitio host.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOINTERFACE`|La interfaz especificada no se admite.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
|`S_FALSE`|No se ha establecido ningún sitio; el parámetro de `ppvSiteObject` se establece en `NULL`.|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)