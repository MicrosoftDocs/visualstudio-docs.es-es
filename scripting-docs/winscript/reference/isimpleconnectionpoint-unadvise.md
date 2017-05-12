---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
Finaliza una conexión de consulta previamente establecida mediante `ISimpleConnectionPoint::Advise`.  
  
## Sintaxis  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### Parámetros  
 `dwCookie`  
 \[in\] token de conexión a finalizar, que devuelve de `ISimpleConnectionPoint::Advise`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Cuando se finaliza una conexión asesor, el punto de conexión llama al método de `Release` en el puntero que se guardó para la conexión durante el método de `ISimpleConnectionPoint::Advise` .  Esa llamada invierte `AddRef` que se realizó durante `ISimpleConnectionPoint::Advise` cuando el punto de conexión llama `QueryInterface`asesor de receptor.  
  
## Vea también  
 [ISimpleConnectionPoint \(Interfaz\)](../../winscript/reference/isimpleconnectionpoint-interface.md)