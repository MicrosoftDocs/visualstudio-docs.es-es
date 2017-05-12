---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
Establece una conexión entre el objeto simple de punto de conexión y el receptor de cliente.  
  
## Sintaxis  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### Parámetros  
 `pdisp`  
 \[in\] el puntero a la interfaz de `IDispatch` en el cliente informa al receptor.  El receptor de cliente recibe llamadas salientes de punto de conexión simple.  
  
 `pdwCookie`  
 \[out\] puntero a un token devuelto que identifica esta conexión.  El llamador utiliza este token más adelante para eliminar la conexión y el método de `ISimpleConnectionPoint::Unadvise` .  Si la conexión no se estableció correctamente, este valor es cero.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método establece una conexión entre el objeto simple de punto de conexión y el receptor de cliente.  
  
## Vea también  
 [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)