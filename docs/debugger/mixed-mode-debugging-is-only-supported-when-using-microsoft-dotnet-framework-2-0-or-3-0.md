---
title: Solo se admite la depuración en modo mixto cuando se usa Microsoft .NET Framework 2.0 o 3.0 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 827d3c5fcc625601019d6cbf61cdbf7c771b63b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929853"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 ó 3.0
Las versiones de Microsoft .NET Framework anteriores a la 2.0 no proporcionan compatibilidad para la depuración en modo mixto de procesos de 64 bits. Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.

 Para evitar este problema, puede:

- Actualizar el proyecto para usar Microsoft .NET Framework 2.0 ó 3.0.

- Depurar el código administrado y el código nativo en sesiones de depuración independientes.

- Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Para cambiar el sistema operativo a 32 bits (Visual Basic o C#)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.

2. En las páginas de propiedades, haga clic en la pestaña **Compilar** o **Depurar**.

3. Haga clic en **Plataforma** y seleccione **x86** en la lista de plataformas.

     De forma predeterminada, los compiladores de C# y Visual Basic generan código que puede ejecutarse en cualquier CPU. En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits. Para ejecutarse en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Para cambiar el sistema operativo a 32 bits (C/C++)

1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.

     En las páginas de propiedades, haga clic en **Plataforma** y seleccione **Win32** en la lista de plataformas.

### <a name="to-correct-this-error"></a>Para corregir este error

- Consulte [configurar la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)