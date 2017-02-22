---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreamData::Next (método)"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un número de registros especificado en el orden indicado.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de registros que se recuperará.  
  
 cbData  
 \[in\]  Tamaño del búfer de datos, en bytes.  
  
 pcbData  
 \[out\]  devuelve el número de bytes devueltos.  Si `data` es NULL, después `pcbData` contiene el número total de bytes de datos disponibles para todos los registros solicitados.  
  
 datos \[\]  
 \[out\]  Un búfer que debe rellenarse con datos del registro de la secuencia de depuración.  
  
 pceltFetched  
 \[in, out\]  Devuelve el número de registros de `data`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay registros.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)