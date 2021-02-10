---
title: DebugBreak y __debugbreak | Microsoft Docs
description: Aprenda a usar la función DebugBreak y el intrínseco __debugbreak para hacer que el programa se interrumpa, como si se hubiera establecido un punto de interrupción.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4fb03cf4d45e367f0d7a99dbe26705475652651
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873150"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak y __debugbreak
Es posible llamar a las funciones [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) de Win32 o [__debugbreak](/cpp/intrinsics/debugbreak) intrínseca en cualquier punto del código. `DebugBreak` y `__debugbreak` tienen el mismo efecto que Establecer un punto de interrupción en dicha posición.

 Como `DebugBreak` es una llamada a una función del sistema, se deben instalar los símbolos de depuración del sistema para asegurarse de que se muestra la información correcta de la pila de llamadas tras una interrupción. De lo contrario, la información de la pila de llamadas mostrada por el depurador podría ser incorrecta. Si utiliza `__debugbreak`, no es necesario ningún símbolo.

## <a name="see-also"></a>Vea también
- [Intrínsecos del controlador](/cpp/intrinsics/compiler-intrinsics)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depuración de código nativo](../debugger/debugging-native-code.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
