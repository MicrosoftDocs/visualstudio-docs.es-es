---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
Devuelve la posición inicial y la longitud de una entrada.  
  
## Sintaxis  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### Parámetros  
 `pichMin`  
 \[out\] objetos que especifican un bloque script, la cual 0 For `IScriptEntry` .  
  
 Para los objetos de `IScriptEntry` que especifican un objeto de función, la cual la posición inicial de la función en el bloque actual del script.  
  
 Para los objetos de `IScriptScriptlet` , retornos 0.  
  
 `pcch`  
 \[out\] objetos que especifican un bloque script, la cual For `IScriptEntry` la longitud del texto.  
  
 Para los objetos de `IScriptEntry` que especifican un objeto de función, la cual la longitud de la definición de función.  
  
 Para los objetos de `IScriptScriptlet` , la cual la longitud de la entrada.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)