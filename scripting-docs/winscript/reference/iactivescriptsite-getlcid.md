---
title: "IActiveScriptSite::GetLCID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetLCID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetLCID"
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetLCID
Recupera el Id. de configuración regional asociado a la interfaz de usuario del host.  El motor de script utiliza el identificador para garantizar que las cadenas de error y otros elementos de interfaz de usuario generados por el motor aparecen en el idioma correspondiente.  
  
## Sintaxis  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### Parámetros  
 `plcid`  
 \[out\] la dirección de una variable que recibe el Id. de configuración regional para elementos de interfaz de usuario mostrados por el motor de script.  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|Este método no está implementado.  Utilice la configuración regional sistema\-definido.|  
|`E_POINTER`|Un puntero no válido se especificado.|  
  
## Comentarios  
 Si este método devuelve `E_NOTIMPL`, el Id. de configuración regional sistema\- definido se debe utilizar.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)