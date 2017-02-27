---
title: "IDiaFrameData::get_virtualAddress | Microsoft Docs"
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
  - "IDiaFrameData::get_virtualAddress (método)"
ms.assetid: de137bee-132f-4aae-a067-9578b7a3e6d4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la dirección virtual \(VA\) de código para el cuadro.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve la dirección virtual de código para el cuadro.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)