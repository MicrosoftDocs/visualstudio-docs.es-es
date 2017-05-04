---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite (interfaz)"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Implementado por el host para crear un sitio para el motor de scripts de Windows.  Normalmente, este sitio estará asociado al contenedor de todos los objetos que son visibles para el script \(por ejemplo, Controles ActiveX\).  Normalmente, este contenedor corresponderá al documento o la página que es vista.  Microsoft Internet Explorer, por ejemplo, crearía un contenedor para cada página HTML que se muestra.  El cada control ActiveX \(u otro objeto de automatización\) en la página, y el motor propio de script, se enumerable dentro de este contenedor.  
  
## métodos en el orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera el Id. de configuración regional que usa el host para mostrar los elementos de la interfaz de usuario.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Obtiene información sobre un elemento que se agregó un motor con una llamada al método de [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una cadena host\- definido que identifica de forma única la versión del documento actual desde el punto de vista de host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Se llama cuando el script ha completado la ejecución.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa al host que el motor de script ha cambiado a estados.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa al host que un error de ejecución producido mientras el motor ejecuta el script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa al host que ha iniciado el motor de script ejecutando el script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa al host que el motor de script cambia de ejecutar script.|  
  
## Vea también  
 [Active Script \(Interfaces\)](../../winscript/reference/active-script-interfaces.md)