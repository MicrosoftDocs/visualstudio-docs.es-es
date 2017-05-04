---
title: "ISimpleConnectionPoint::GetEventCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.GetEventCount
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::GetEventCount"
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::GetEventCount
Devuelve el número de eventos expuestos en esta interfaz.  
  
## Sintaxis  
  
```  
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### Parámetros  
 `pulCount`  
 \[out\] número de eventos expuestos en este recuento de interfaz.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el número de eventos expuestos en esta interfaz.  
  
## Vea también  
 [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)