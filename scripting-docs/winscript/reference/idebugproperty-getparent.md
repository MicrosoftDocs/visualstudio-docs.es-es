---
title: "IDebugProperty::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetParent"
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetParent
obtiene la propiedad parent de una propiedad.  
  
## Sintaxis  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### Parámetros  
 `ppParent`  
 \[out\] devuelve la interfaz de `IDebugProperty` que representa el elemento primario de la propiedad.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)