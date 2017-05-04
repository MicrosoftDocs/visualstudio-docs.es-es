---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
Devuelve un enumerador de los marcos de pila del subproceso actual.  
  
## Sintaxis  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parámetros  
 `dwSpMin`  
 \[in\] límite inferior de la dirección para obtener una lista de los marcos de pila.  
  
 `ppedsf`  
 \[out\] enumerador de los marcos de pila del subproceso actual.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El enumerador del marco de pila devuelve los marcos que comienza en la parte superior de la pila, con el cuadro recientemente presionado.  El enumerador contiene sólo los marcos de pila con direcciones mayor o igual `dwSpMin`.  
  
## Vea también  
 [IDebugStackFrameSnifferEx \(Interfaz\)](../../winscript/reference/idebugstackframesnifferex-interface.md)