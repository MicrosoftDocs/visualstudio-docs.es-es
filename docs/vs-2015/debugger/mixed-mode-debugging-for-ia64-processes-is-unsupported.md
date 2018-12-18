---
title: No se admite la depuración en modo mixto para procesos IA64. | Microsoft Docs
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
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12623f2692735b8a6ec31a4ecaa7bfc0b07e9364
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806469"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>No se admite la depuración en modo mixto para procesos IA64.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio no admite la depuración en modo mixto de código nativo y administrado en procesos IA64. Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.  
  
### <a name="workarounds"></a>Soluciones  
  
-   Depurar el código administrado y el código nativo en sesiones de depuración independientes.  
  
     -O bien-  
  
     Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Para cambiar la plataforma a 32 bits (Visual Basic o C#)  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto y luego haga clic en **propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en el **compilar** o **depurar** ficha.  
  
3.  Haga clic en **plataforma** y seleccione x86 en la lista de plataformas.  
  
     De forma predeterminada, los compiladores de C# y Visual Basic generan código que puede ejecutarse en cualquier CPU. En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits. Para ejecutar en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Para cambiar la plataforma a 32 bits (C/C++)  
  
1.  En **el Explorador de soluciones**, haga doble clic en el proyecto y luego haga clic en **propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en **plataforma** y seleccione Win32 en la lista de plataformas,  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)



