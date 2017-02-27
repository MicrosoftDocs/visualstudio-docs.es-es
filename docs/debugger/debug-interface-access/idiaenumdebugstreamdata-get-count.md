---
title: "IDiaEnumDebugStreamData::get_Count | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumDebugStreamData::get_Count (método)"
ms.assetid: 74ff3a85-3cc2-4aa8-ad9a-7f335b795ed1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los registros del número de la secuencia de datos de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### Parámetros  
 pRetVal  
 \[out, retval\]  devuelve el número de registros.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)