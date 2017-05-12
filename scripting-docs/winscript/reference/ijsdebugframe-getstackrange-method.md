---
title: "IJsDebugFrame::GetStackRange (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange (M&#233;todo)
Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.  
  
## Sintaxis  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### Parámetros  
 `pStart`  
 \[out\] Puntero de pila base del marco.  
  
 `pEnd`  
 \[out\] Puntero de apilador superior del marco.  
  
## Valor devuelto  
  
## Comentarios  
 Este método es útil para juntar los seguimientos de pila intercalados recopilados a partir de varios runtimes.  Los punteros de pila iniciales y finales pueden abarcar varios marcos de pila de máquina física \(para los marcos en tiempo de ejecución de JavaScript interpretados\). Empiece \> termine conforme la pila crece desde la dirección alta a la baja.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugFrame \(Interfaz\)](../../winscript/reference/ijsdebugframe-interface.md)