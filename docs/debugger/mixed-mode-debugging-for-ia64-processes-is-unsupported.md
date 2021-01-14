---
title: No se admite la depuración en modo mixto de procesos IA64
description: Visual Studio no admite la depuración en modo mixto de código nativo y administrado en procesos IA64 (Itanium). Consulte este artículo para conocer las soluciones alternativas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65969e354a5d1ed2dc1cf54ca31e6088cc19de7a
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975256"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>No se admite la depuración en modo mixto para procesos IA64.
Visual Studio no admite la depuración en modo mixto de código nativo y administrado en procesos IA64. Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.

### <a name="workarounds"></a>Soluciones

- Depurar el código administrado y el código nativo en sesiones de depuración independientes.

     o bien

     Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para cambiar la plataforma a 32 bits (Visual Basic o C#)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.

2. En las páginas de propiedades, haga clic en la pestaña **Compilar** o **Depurar**.

3. Haga clic en **Plataforma** y seleccione x86 en la lista de plataformas.

     De forma predeterminada, los compiladores de C# y Visual Basic generan código que puede ejecutarse en cualquier CPU. En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits. Para ejecutarse en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Para cambiar la plataforma a 32 bits (C/C++)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.

2. En las páginas de propiedades, haga clic en **Plataforma** y seleccione Win32 en la lista de plataformas.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)