---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
Establece el nombre de elemento que identifica un objeto de `IScriptEntry` .  
  
## Sintaxis  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] dirección de un búfer que contiene el nombre del elemento.  El nombre de elemento utilizan el host para identificar la entrada.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no se realizó correctamente.|  
  
## Comentarios  
 Para los objetos de `IScriptEntry` , este método devuelve `S_OK`.  
  
 Para los objetos de `IScriptScriptlet` \(que se derivan de `IScriptEntry`\), este método devuelve `E_FAIL`.  Para los objetos de `IScriptScriptlet` , el nombre de elemento es establecido por [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) y no se puede cambiar.  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)