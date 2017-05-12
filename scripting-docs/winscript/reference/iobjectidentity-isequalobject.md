---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject (método)"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
Determina si un objeto es igual al objeto actual.  
  
## Sintaxis  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### Parámetros  
 `punk`  
 \[in\] dirección del objeto que se va a comparar con el objeto actual.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|Los objetos son iguales.|  
|`S_FALSE`|Los objetos no son iguales.|  
  
## Comentarios  
 Una implementación del método de `IsEqualObject` debe devolver `S_OK` sólo si los objetos son idénticos.  
  
## Vea también  
 [IObjectIdentity \(Interfaz\)](../../winscript/reference/iobjectidentity-interface.md)