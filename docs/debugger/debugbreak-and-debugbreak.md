---
title: "DebugBreak y __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "puntos de interrupción, DebugBreak (función)"
  - "DebugBreak (función)"
  - "depurar [C++], DebugBreak (función)"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# DebugBreak y __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La función DebugBreak de Win32 o la función [](/visual-cpp/intrinsics/debugbreak) intrínseca se puede llamar en cualquier punto del código.  `DebugBreak` y `__debugbreak` tienen el mismo efecto que Establecer un punto de interrupción en dicha posición.  
  
 Como `DebugBreak` es una llamada a una función del sistema, se deben instalar los símbolos de depuración del sistema para asegurarse de que se muestra la información correcta de la pila de llamadas tras una interrupción.  De lo contrario, la información de la pila de llamadas mostrada por el depurador podría ser incorrecta.  Si utiliza `__debugbreak`, no es necesario ningún símbolo.  
  
## Vea también  
 [Intrínsecos del controlador](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)