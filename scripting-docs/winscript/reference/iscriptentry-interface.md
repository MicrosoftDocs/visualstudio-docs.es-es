---
title: "IScriptEntry (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptEntry (interfaz)"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry (Interfaz)
Un objeto que implementa la interfaz de `IScriptEntry` representa un bloque de script o un objeto de función.  
  
 Además de los métodos heredados de `IScriptNode`, la interfaz `IScriptEntry` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Devuelve el texto que corresponde al cuerpo de un bloque de script de `IScriptEntry` , de bloque de función, o de scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Devuelve el nombre de elemento que identifica un objeto de `IScriptEntry` .|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Para las entradas que representan un objeto único \(como una función\), especificado el nombre del objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Devuelve la posición inicial y la longitud de una entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Información de tipo de retornos para un objeto de función de `IScriptEntry` .|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Devuelve el texto que corresponde a un bloque de script de `IScriptEntry` , o el código fuente que contenga un controlador de eventos de `IScriptScriptlet` .|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Establece el texto incluido en el cuerpo de un bloque de script de `IScriptEntry` o un scriptlet de `IScriptScriptlet` .|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Establece el nombre de elemento que identifica un objeto de `IScriptEntry` .|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Para las entradas que representan un objeto único \(como una función\), establece el nombre del objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Establece la información de tipo para un objeto de función de `IScriptEntry` .|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Establece el texto que corresponde a un bloque de script de `IScriptEntry` , o el código fuente que contenga un controlador de eventos de `IScriptScriptlet` .|  
  
## Vea también  
 [Active Script Authoring \(Interfaces\)](../../winscript/reference/active-script-authoring-interfaces.md)