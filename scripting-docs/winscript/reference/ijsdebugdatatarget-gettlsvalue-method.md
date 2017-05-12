---
title: "IJsDebugDataTarget::GetTlsValue (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue (M&#233;todo)
Para el subproceso que se está depurando, recupera el valor en la ranura del almacenamiento local de subprocesos \(TLS\) para el índice especificado de TLS.  
  
## Sintaxis  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### Parámetros  
 `threadId`  
 \[in\] Subproceso que se está ejecutando en el proceso de destino a leer.  
  
 `tlsIndex`  
 \[in\] Índice TLS asignado cuando el proceso de destino llamó a la función TlsAlloc.  
  
 `pValue`  
 \[out\] Valor dimensionado por puntero que se almacenó en la ranura TLS de subprocesos.  Si el subproceso de destino es de 32 bits, los 32 bits por encima de este valor serán cero.  
  
## Valor devuelto  
  
## Comentarios  
 Cada subproceso de un proceso tiene su propia ranura para cada índice de TLS.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugDataTarget \(Interfaz\)](../../winscript/reference/ijsdebugdatatarget-interface.md)