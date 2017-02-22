---
title: "El modo de depuraci&#243;n mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 &#243; 3.0 | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# El modo de depuraci&#243;n mixto se admite solo cuando se usa Microsoft .NET Framework 2.0 &#243; 3.0
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las versiones de Microsoft .NET Framework anteriores a la 2.0 no proporcionan compatibilidad para la depuración en modo mixto de procesos de 64 bits.  Esto significa que no puede pasar de código administrado a código nativo, o de código nativo a código administrado, mientras está depurando.  
  
 Para evitar este problema, puede:  
  
-   Actualizar el proyecto para usar Microsoft .NET Framework 2.0 ó 3.0.  
  
-   Depurar el código administrado y el código nativo en sesiones de depuración independientes.  
  
-   Depurar el código mixto como un proceso de 32 bits, tal y como se describe en los procedimientos siguientes.  
  
### Para cambiar el sistema operativo a 32 bits \(Visual Basic o C\#\)  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.  
  
2.  En las páginas de propiedades, haga clic en la pestaña **Compilar** o **Depurar**.  
  
3.  Haga clic en **Plataforma** y seleccione **x86** en la lista de plataformas.  
  
     De forma predeterminada, los compiladores de C\# y Visual Basic generan código que puede ejecutarse en cualquier CPU.  En un equipo de 64 bits, estos archivos binarios se ejecutan como procesos de 64 bits.  Para ejecutarse en un proceso de 32 bits, debe elegir **Win32**, no **AnyCPU**.  
  
### Para cambiar el sistema operativo a 32 bits \(C\/C\+\+\)  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, haga clic en **Propiedades** en el menú contextual.  
  
     En las páginas de propiedades, haga clic en **Plataforma** y seleccione **Win32** en la lista de plataformas.  
  
### Para corregir este error  
  
-   Vea [Setting Up SQL Debugging](http://msdn.microsoft.com/es-es/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Vea también  
 [Depurar aplicaciones de 64 bits](../debugger/debug-64-bit-applications.md)