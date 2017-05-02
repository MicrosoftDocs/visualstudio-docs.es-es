---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
Devuelve el texto que corresponde al cuerpo de un bloque de script de `IScriptEntry` , de bloque de función, o de scriptlet.  
  
## Sintaxis  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### Parámetros  
 `pbstr`  
 \[out\] texto a El que está en el cuerpo de una de las acciones siguientes:  
  
-   Un bloque de script de `IScriptEntry`  
  
-   Una función de `IScriptEntry` en un bloque de función  
  
-   Un controlador de eventos de scriptlet de `IScriptEntry`  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)