---
title: "Optimizaci&#243;n y depuraci&#243;n JIT | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], código optimizado"
  - "código optimizado, depurar"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Optimizaci&#243;n y depuraci&#243;n JIT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se depura una aplicación administrada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] suprime de forma predeterminada la optimización del código Just\-In\-Time \(JIT\).  Suprimir la optimización JIT significa que se está depurando código no optimizado.  El código se ejecuta un poco más lentamente porque no se optimiza, pero la experiencia de depuración es mucho más profunda.  La depuración de código optimizado es más difícil, y sólo se recomienda si se detecta un error en el código optimizado que no se puede reproducir en la versión no optimizada.  
  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la optimización JIT se controla por medio de la opción **Suprimir optimización JIT al cargar el módulo**.  Puede encontrarla en la página **General**, bajo el nodo **Depuración** del cuadro de diálogo **Opciones**.  
  
 Si desactiva la opción **Suprimir optimización JIT al cargar el módulo**, puede depurar código JIT optimizado, pero su capacidad de depuración puede ser limitada debido a que el código optimizado no coincide con el código fuente.  Como resultado, puede que las ventanas del depurador como **Variables locales** y **Automático** no muestren tanta información como si se depurara código no optimizado.  
  
 Otra diferencia importante es relativa a la depuración con Sólo mi código.  Si se depura con Sólo mi código, el depurador considera que el código optimizado no es del usuario, por lo que no debería mostrarse durante la depuración.  Por consiguiente, si depura código optimizado JIT, probablemente desee desactivar Sólo mi código.  Para obtener más información, vea [Restringir la ejecución paso a paso a Solo mi código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Recuerde que la opción **Suprimir optimización JIT al cargar el módulo** suprime la optimización del código cuando se cargan los módulos.  Si se asocia a un proceso que ya se está ejecutando, éste puede contener código que ya esté cargado, con compilación y optimización JIT.  La opción **Suprimir optimización JIT al cargar el módulo** no afecta a este tipo de código, pero sí a los módulos que se cargan después de la asociación.  Además, la opción **Suprimir optimización JIT al cargar el módulo** no afecta a los módulos, como WinForms.dll, que se crean con NGEN.  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proceso de ejecución administrada](../Topic/Managed%20Execution%20Process.md)