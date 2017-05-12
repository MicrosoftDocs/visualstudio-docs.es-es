---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow (interfaz)"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
Esta interfaz se implementa por hosts que admiten una interfaz de usuario en el mismo objeto que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  Los hosts que no admitan una interfaz de usuario, como servidores, no implementarían la interfaz de `IActiveScriptSiteWindow` .  El motor de script tiene acceso a esta interfaz llamando a `QueryInterface` de `IActiveScriptSite`.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera el identificador de ventana que puede actuar como el propietario de una ventana emergente que el motor de script debe mostrar.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Hace que el host para habilitar o deshabilitar la ventana principal así como cualquier cuadro de diálogo no modal.|  
  
## Vea también  
 [Active Script \(Interfaces\)](../../winscript/reference/active-script-interfaces.md)