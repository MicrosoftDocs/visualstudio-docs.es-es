---
title: "No se admite la depuraci&#243;n en modo mixto para procesos IA64. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_ia64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# No se admite la depuraci&#243;n en modo mixto para procesos IA64.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio no admite la depuración en modo mixto de código nativo y administrado en procesos IA64.  Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.  
  
### Soluciones  
  
-   Depurar el código administrado y el código nativo en sesiones de depuración independientes.  
  
     O bien  
  
     Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.  
  
### Para cambiar la plataforma a 32 bits \(Visual Basic o C\#\)  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en la pestaña **Compilar** o **Depurar**.  
  
3.  Haga clic en **Plataforma** y seleccione x86 en la lista de plataformas.  
  
     De forma predeterminada, los compiladores de C\# y Visual Basic generan código que puede ejecutarse en cualquier CPU.  En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits.  Para ejecutarse en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.  
  
### Para cambiar la plataforma a 32 bits \(C\/C\+\+\)  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en **Plataforma** y seleccione Win32 en la lista de plataformas.  
  
## Vea también  
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)