---
title: "IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::CreateDebugDocumentHelper"
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::CreateDebugDocumentHelper
Crea una nueva aplicación auxiliar de depuración para esta aplicación.  
  
## Sintaxis  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### Parámetros  
 `punkOuter`  
 \[in\] si el objeto devuelto a agregar, `punkOuter` es un puntero de interfaz a `IUnknown`que controla.  Si no, es un puntero NULL.  
  
 `pddh`  
 \[out\] objeto auxiliar de depuración para obtener esta aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea una nueva aplicación auxiliar de depuración para esta aplicación.  
  
## Vea también  
 [IProcessDebugManager \(Interfaz\)](../../winscript/reference/iprocessdebugmanager-interface.md)