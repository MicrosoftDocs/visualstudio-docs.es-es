---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
Recupera el identificador de una ventana que pueda actuar como propietaria de una ventana emergente que el motor de script debe mostrar.  
  
## Sintaxis  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### Parámetros  
 `phwnd`  
 \[out\] dirección de una variable que recibe el identificador de ventana.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL` si se ha producido un error.  
  
## Comentarios  
 Este método es similar al método `IOleWindow::GetWindow`.  
  
## Vea también  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)