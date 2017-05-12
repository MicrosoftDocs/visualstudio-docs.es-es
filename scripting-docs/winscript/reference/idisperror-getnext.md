---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
Recupera el objeto siguiente de `IDispError` .  
  
## Sintaxis  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### Parámetros  
 `ppde`  
 \[out\] especifica el siguiente objeto de `IDispError` .  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método recupera el siguiente objeto de `IDispError` .  Si éste es el último objeto de `IDispError` , retornos NULL de este método.  
  
> [!NOTE]
>  Este método no está implementado.  
  
## Vea también  
 [IDispError \(Interfaz\)](../../winscript/reference/idisperror-interface.md)