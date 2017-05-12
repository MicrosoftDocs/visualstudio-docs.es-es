---
title: "IApplicationDebugger::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::QueryAlive"
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::QueryAlive
Indica si el depurador está respondiendo.  
  
## Sintaxis  
  
```  
HRESULT QueryAlive();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método indica si el depurador está respondiendo.  Las implementaciones de este método siempre deben devolver `S_OK`.  
  
 Si el proceso del depurador finaliza inesperadamente, COM devuelve un error de proxy que forma para las llamadas a este método.  
  
## Vea también  
 [IApplicationDebugger \(Interfaz\)](../../winscript/reference/iapplicationdebugger-interface.md)