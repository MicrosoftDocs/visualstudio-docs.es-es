---
title: DebugBreak y __debugbreak | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c4b9d780caf7589eecdc709cbede577dd7a6fd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686163"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak y __debugbreak
La función DebugBreak de Win32 o la función [__debugbreak](/cpp/intrinsics/debugbreak) intrínseca se puede llamar en cualquier punto del código. `DebugBreak` y `__debugbreak` tienen el mismo efecto que Establecer un punto de interrupción en dicha posición.

 Como `DebugBreak` es una llamada a una función del sistema, se deben instalar los símbolos de depuración del sistema para asegurarse de que se muestra la información correcta de la pila de llamadas tras una interrupción. De lo contrario, la información de la pila de llamadas mostrada por el depurador podría ser incorrecta. Si utiliza `__debugbreak`, no es necesario ningún símbolo.

## <a name="see-also"></a>Vea también
- [Intrínsecos del controlador](/cpp/intrinsics/compiler-intrinsics)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)