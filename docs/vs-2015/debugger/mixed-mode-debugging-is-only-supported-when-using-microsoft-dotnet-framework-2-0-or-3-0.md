---
title: Solo se admite la depuración en modo mixto cuando se usa Microsoft .NET Framework 2.0 o 3.0 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 1248ab59841ccd2861507bbf075fcbeb93959ae4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753051"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>El modo de depuración mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 ó 3.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las versiones de Microsoft .NET Framework anteriores a la 2.0 no proporcionan compatibilidad para la depuración en modo mixto de procesos de 64 bits. Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.  
  
 Para evitar este problema, puede:  
  
-   Actualizar el proyecto para usar Microsoft .NET Framework 2.0 ó 3.0.  
  
-   Depurar el código administrado y el código nativo en sesiones de depuración independientes.  
  
-   Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Para cambiar el sistema operativo a 32 bits (Visual Basic o C#)  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en el **compilar** o **depurar** ficha.  
  
3.  Haga clic en **plataforma**y, a continuación, seleccione **x86** en la lista de plataformas.  
  
     De forma predeterminada, los compiladores de C# y Visual Basic generan código que puede ejecutarse en cualquier CPU. En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits. Para ejecutar en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Para cambiar el sistema operativo a 32 bits (C/C++)  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades** en el menú contextual.  
  
     En las páginas de propiedades, haga clic en **plataforma**y, a continuación, seleccione **Win32** en la lista de plataformas.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Consulte [configurar la depuración de SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)



