---
title: "IJsDebugDataTarget::ReadNullTerminatedString (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString (M&#233;todo)
Lee el número especificado de caracteres del destino.  
  
## Sintaxis  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### Parámetros  
 `address`  
 \[in\] Dirección de la que leer.  
  
 `characterSize`  
 \[in\] tamaño de cada carácter de la cadena  
  
 `maxCharacters`  
 \[in\] Número máximo de caracteres a leer. maxCharacters debe ser razonable.  Cualquier solicitud de más de 128 MB de memoria producirá un error.  Si la cadena es mayor que maxCharacters, la cadena de resultado se trucará después de maxCharacters.  
  
 `pString`  
 \[out\] BSTR leído del destino.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve S\_FALSE si se trunca.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)