---
title: "IEnumDebugExpressionContexts::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Clone"
ms.assetid: c8070ae1-120c-4b5d-bd3d-ae8fca6f9277
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Clone
Crea un enumerador que contiene el mismo estado que el enumerador actual.  
  
## Sintaxis  
  
```  
HRESULT Clone(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parámetros  
 `ppedec`  
 \[out\] devuelve la interfaz de `IEnumDebugExpressionContexts` clone de enumerador.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea un enumerador que contiene al mismo estado que el enumerador actual.  
  
## Vea también  
 [IEnumDebugExpressionContexts \(Interfaz\)](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)