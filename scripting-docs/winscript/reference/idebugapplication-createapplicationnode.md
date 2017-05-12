---
title: "IDebugApplication::CreateApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateApplicationNode"
ms.assetid: 1a1414f6-df14-4c56-b39a-8384cf16174a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateApplicationNode
Crea un nodo de aplicación asociado a un proveedor de documento concreto.  
  
## Sintaxis  
  
```  
HRESULT CreateApplicationNode(  
   IDebugApplicationNode**  ppdanNew  
);  
```  
  
#### Parámetros  
 `ppdanNew`  
 \[out\] nodo de aplicación de El asociado a este proveedor de documento.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El nodo de la nueva aplicación no es visible hasta que se asocia a un nodo primario.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)