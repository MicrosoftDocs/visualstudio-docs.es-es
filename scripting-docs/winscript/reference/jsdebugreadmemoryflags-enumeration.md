---
title: "JsDebugReadMemoryFlags (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags (Enumeraci&#243;n)
Marcas para especificar el comportamiento al leer la memoria.  
  
## Sintaxis  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Members  
  
### Valores  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que el llamador desea que la operación de lectura se realice correctamente si solo parte de la lectura de memoria se realizó correctamente.  Si se establece, se produce un error E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si 'Direcciones' no es válido.  Si esta marca está desactivada, se producirá un error E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS si cualquier parte de la memoria solicitada no se puede leer.|  
|`None`|Indica que el llamador desea el comportamiento predeterminado para ReadMemory.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)