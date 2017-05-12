---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
Información de tipo de retornos para un objeto de función de `IScriptEntry` .  
  
## Sintaxis  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### Parámetros  
 `ppti`  
 \[out\] información de tipo asociada a este objeto de función de `IScriptEntry` .  
  
 `piMethod`  
 \[out\] índice del objeto de `ITypeInfo` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Se escribe información de tipo establecida mediante [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  La información de tipo también se puede generar mediante la entrada basada en la representación interna de la función.  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)