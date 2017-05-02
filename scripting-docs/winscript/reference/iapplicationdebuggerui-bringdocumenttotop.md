---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
Trae la ventana que contiene el documento especificado de depuración a la parte superior de la interfaz de usuario del depurador.  
  
## Sintaxis  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### Parámetros  
 `pddt`  
 \[in\] depurar el documento para llevar a la parte superior de la interfaz de usuario del depurador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|El documento no se conoce.|  
  
## Comentarios  
 Este método devuelve la ventana que contiene el documento especificado de depuración a la parte superior de la interfaz de usuario del depurador.  
  
## Vea también  
 [IApplicationDebuggerUI \(Interfaz\)](../../winscript/reference/iapplicationdebuggerui-interface.md)