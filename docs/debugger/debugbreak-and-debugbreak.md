---
title: DebugBreak y __debugbreak | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d76b4a08c90b3ae37832da97e0615282c0f11d67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak y __debugbreak
Puede llamar a la función DebugBreak de Win32 o la [__debugbreak](/cpp/intrinsics/debugbreak) intrínseco en cualquier momento en el código. `DebugBreak` y `__debugbreak` tienen el mismo efecto que Establecer un punto de interrupción en dicha posición.  
  
 Como `DebugBreak` es una llamada a una función del sistema, se deben instalar los símbolos de depuración del sistema para asegurarse de que se muestra la información correcta de la pila de llamadas tras una interrupción. De lo contrario, la información de la pila de llamadas mostrada por el depurador podría ser incorrecta. Si utiliza `__debugbreak`, no es necesario ningún símbolo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](/cpp/intrinsics/compiler-intrinsics)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)