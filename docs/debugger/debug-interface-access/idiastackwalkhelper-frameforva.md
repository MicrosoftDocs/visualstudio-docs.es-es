---
title: "IDiaStackWalkHelper::frameForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::frameForVA (método)"
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::frameForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el marco de pila que contiene la dirección virtual especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT frameForVA(   
   ULONGLONG        va,  
   IDiaFrameData**  ppFrame  
);  
```  
  
#### Parámetros  
 `va`  
 \[in\]  La dirección virtual para los datos del cuadro.  
  
 `ppFrame`  
 \[out\]  un objeto de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa el marco de pila en la dirección especificada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)