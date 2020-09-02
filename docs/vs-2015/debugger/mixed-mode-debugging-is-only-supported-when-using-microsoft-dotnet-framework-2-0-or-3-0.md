---
title: El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 ó 3.0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc45927ad6cc1189ed1d08328b4dd362821cdcb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696466"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 ó 3.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
- Vea [Configuración de la depuración de SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Consulte también  
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)
