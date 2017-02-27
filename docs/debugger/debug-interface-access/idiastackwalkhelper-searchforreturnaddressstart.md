---
title: "IDiaStackWalkHelper::searchForReturnAddressStart | Microsoft Docs"
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
  - "IDiaStackWalkHelper::searchForReturnAddressStart (método)"
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

busca el marco de pila especificado para un remite en o cerca de la dirección especificada de la pila.  
  
## Sintaxis  
  
```cpp#  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### Parámetros  
 `frame`  
 \[in\]  un objeto de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa el marco de pila actual.  
  
 `startAddress`  
 \[in\]  Una dirección de memoria virtual que empezar a buscar.  
  
 `ReturnAddress`  
 \[out\]  Devuelve el remite más próximo de la función a `startAddress`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)