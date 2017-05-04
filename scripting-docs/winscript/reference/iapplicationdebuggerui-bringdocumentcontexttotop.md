---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
Trae la ventana que contiene el contexto determinado del documento en la parte superior de la interfaz de usuario del depurador y desplaza la ventana al contexto.  
  
## Sintaxis  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### Parámetros  
 `pddc`  
 \[in\] documente el contexto para llevar a la parte superior de la interfaz de usuario del depurador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|El contexto especificado por `pddc` no se conoce.|  
  
## Comentarios  
 Este método devuelve la ventana que contiene el contexto determinado del documento en la parte superior de la interfaz de usuario del depurador y desplaza la ventana al contexto.  
  
## Vea también  
 [IApplicationDebuggerUI \(Interfaz\)](../../winscript/reference/iapplicationdebuggerui-interface.md)