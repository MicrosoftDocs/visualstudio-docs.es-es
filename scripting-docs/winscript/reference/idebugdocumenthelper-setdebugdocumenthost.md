---
title: "IDebugDocumentHelper::SetDebugDocumentHost | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDebugDocumentHost
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDebugDocumentHost"
ms.assetid: b26a03c3-8a3f-47b0-b916-4c65d5500f10
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDebugDocumentHost
Establece `IDebugDocumentHost` para este documento.  
  
## Sintaxis  
  
```  
HRESULT SetDebugDocumentHost(  
   IDebugDocumentHost*  pddh  
);  
```  
  
#### Parámetros  
 `pddh`  
 \[in\] host document de depuración de El.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 La interfaz de `IDebugDocumentHost` se utiliza para el color de la sintaxis de host inteligente, capturar el texto aplazada, y volver a los objetos para los contextos creados recientemente del documento.  
  
## Vea también  
 [IDebugDocumentHelper \(Interfaz\)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHost \(Interfaz\)](../../winscript/reference/idebugdocumenthost-interface.md)