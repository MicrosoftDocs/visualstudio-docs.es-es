---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
Devuelve el número de línea y, opcionalmente, el desplazamiento del carácter en la línea que corresponde a la posición de caracteres determinada.  
  
## Sintaxis  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### Parámetros  
 `cCharacterPosition`  
 \[in\] ubicación de inicio del intervalo de la posición.  
  
 `pcLineNumber`  
 \[out\] número de línea del intervalo.  
  
 `pcCharacterOffsetInLine`  
 \[in, out\] desplazamiento de caracteres del intervalo de la línea `pcLineNumber`.  Si este parámetro es `NULL`, el método no devuelve un valor.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el número de línea y, opcionalmente, el desplazamiento del carácter en la línea que corresponde a la posición de caracteres determinada.  
  
## Vea también  
 [IDebugDocumentText \(Interfaz\)](../../winscript/reference/idebugdocumenttext-interface.md)