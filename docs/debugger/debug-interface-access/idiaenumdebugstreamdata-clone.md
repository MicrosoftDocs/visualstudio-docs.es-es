---
title: "IDiaEnumDebugStreamData::Clone | Microsoft Docs"
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
  - "IDiaEnumDebugStreamData::Clone (método)"
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumDebugStreamData::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un enumerador que contiene el mismo orden que el enumerador actual.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreamData** ppenum  
);  
```  
  
#### Parámetros  
 ppenum  
 \[out\]  Devuelve un objeto de [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) que contiene la secuencia duplicada de registros de la secuencia de datos de depuración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)