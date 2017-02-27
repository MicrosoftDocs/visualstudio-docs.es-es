---
title: "IDiaEnumFrameData::frameByVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByVA (método)"
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumFrameData::frameByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve un cuadro dirección virtual \(VA\).  
  
## Sintaxis  
  
```cpp#  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### Parámetros  
 virtualAddress  
 \[in\]  VA del marco de interés.  
  
 cuadro  
 \[out\]  Devuelve un objeto de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa el cuadro que contiene la dirección proporcionada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si ninguna coincidencia de los datos del cuadro la dirección especificada.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)