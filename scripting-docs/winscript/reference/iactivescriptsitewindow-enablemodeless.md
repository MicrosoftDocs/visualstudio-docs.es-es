---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
Hace que el host para habilitar o deshabilitar la ventana principal así como cualquier cuadro de diálogo no modal.  
  
## Sintaxis  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### Parámetros  
 `fEnable`  
 \[in\] marca que, si `TRUE`, habilita la ventana principal y cuadros de diálogo no modales o, si `FALSE`, se deshabilitan.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL`si se ha producido un error.  
  
## Comentarios  
 Este método es idéntico al método de `IOleInPlaceFrame::EnableModeless` .  
  
 Las llamadas a este método se pueden anidar.  
  
## Vea también  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)