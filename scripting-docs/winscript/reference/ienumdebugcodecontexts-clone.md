---
title: "IEnumDebugCodeContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Clone"
ms.assetid: eaad6af9-4a0a-49c9-8f73-bccaa42b235c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Clone
Crea un enumerador que contiene el mismo estado que el enumerador actual.  
  
## Sintaxis  
  
```  
HRESULT Clone(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parámetros  
 `ppescc`  
 \[out\] devuelve la interfaz de `IEnumDebugCodeContexts` clone de enumerador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea un enumerador que contiene al mismo estado que el enumerador actual.  
  
## Vea también  
 [IEnumDebugCodeContexts \(Interfaz\)](../../winscript/reference/ienumdebugcodecontexts-interface.md)