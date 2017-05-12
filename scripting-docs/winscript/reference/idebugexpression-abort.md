---
title: "IDebugExpression::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Abort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Abort"
ms.assetid: dbdb63c1-6c4a-4cef-bb40-1843495ae167
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Abort
Detiene la expresión.  
  
## Sintaxis  
  
```  
HRESULT Abort();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método detiene una evaluación de la expresión en la primera oportunidad.  
  
## Vea también  
 [IDebugExpression \(Interfaz\)](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)