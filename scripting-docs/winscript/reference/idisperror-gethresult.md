---
title: "IDispError::GetHresult | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHresult"
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHresult
Recupera el código de error del objeto de `IDispError` .  
  
## Sintaxis  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### Parámetros  
 `phr`  
 \[out\] especifica el código de error.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera el código de error del objeto de `IDispError` .  
  
> [!NOTE]
>  Este método no está implementado.  
  
## Vea también  
 [IDispError \(Interfaz\)](../../winscript/reference/idisperror-interface.md)