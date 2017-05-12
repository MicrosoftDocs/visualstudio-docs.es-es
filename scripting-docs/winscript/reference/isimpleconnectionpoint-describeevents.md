---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
Devuelve el identificador de envío y el nombre de cada evento en un intervalo especificado de eventos.  
  
## Sintaxis  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### Parámetros  
 `iEvent`  
 \[in\] índice del primer evento a recuperar.  
  
 `cEvents`  
 \[in\] número de eventos que se va a recuperar.  
  
 `prgid`  
 \[out\] matriz de valores de evento DISPID.  
  
 `prgbstr`  
 \[out\] matriz de nombres de evento.  
  
 `pcEventsFetched`  
 \[out\] número real de eventos capturados.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`S_FALSE`|Más eventos se solicitaron disponible.  Los eventos no disponible se representan con DISPID\_NULL y BSTR null.|  
|`E_INVALIDARG`|Ningún elemento podrían ser capturados.|  
  
## Comentarios  
 Este método devuelve el identificador de envío y el nombre de cada evento en un intervalo especificado de eventos.  
  
## Vea también  
 [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)