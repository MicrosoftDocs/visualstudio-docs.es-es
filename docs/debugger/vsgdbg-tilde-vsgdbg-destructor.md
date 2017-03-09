---
title: "VsgDbg::~VsgDbg (Destructor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (Destructor)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Destruye una instancia de la clase `VsgDbg`.  Si se está grabando activamente información de gráficos, el archivo de registro de gráficos se finaliza y se cierra, y se liberan los recursos utilizados mientras se capturaba activamente información de gráficos.  
  
## Sintaxis  
  
```cpp  
~VsgDbg();  
```  
  
## Vea también  
 [VsgDbg::VsgDbg \(Constructor\)](../debugger/vsgdbg-vsgdbg-constructor.md)