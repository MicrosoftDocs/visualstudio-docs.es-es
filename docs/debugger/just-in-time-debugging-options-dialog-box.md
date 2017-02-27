---
title: "Just-In-Time, Depuraci&#243;n, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.JIT"
  - "vs.debug.options.JIT"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Depuración Just-In-Time, establecer opciones"
  - "Cuadro de diálogo Opciones, depuración"
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Just-In-Time, Depuraci&#243;n, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para obtener acceso a la página **Just\-In\-Time**, vaya al menú **Herramientas** y haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, expanda el nodo **Depuración** y seleccione **Just\-In\-Time**.  Esta página permite habilitar la depuración Just\-In\-Time para el código administrado, código nativo y scripts.  Para obtener más información, vea [Depuración Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Puede habilitar la depuración Just\-In\-Time para estos tipos de programas:  
  
-   Administrado  
  
-   Nativo  
  
-   Script  
  
 La depuración Just\-In\-Time es una técnica para depurar un programa iniciado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Puede ejecutar un sistema creado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fuera del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si ha habilitado la depuración Just\-In\-Time, un bloqueo mostrará un cuadro de diálogo en el que se le preguntará si desea depurar.  
  
## Advertencias asociadas  
 Cuando visite esta página del cuadro de diálogo **Opciones**, es posible que aparezca un mensaje de advertencia como este:  
  
 **Otro depurador se ha registrado como el depurador Just\-In\-Time.  Para reparar, habilite la depuración Just\-In\-Time o ejecute la reparación de Visual Studio.**  
  
 Este mensaje aparece si hay otro depurador, posiblemente una versión anterior del depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definido como el depurador Just\-In\-Time.  
  
 Otro mensaje que podría ver es el siguiente:  
  
 **Errores de registro de la depuración Just\-In\-Time.  Para reparar, habilite la depuración Just\-In\-Time o ejecute la reparación de Visual Studio.**  
  
 Si aparece cualquiera de estas advertencias, la depuración Just\-In\-Time con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] requiere privilegios de administrador hasta que se corrija el problema.  Si intenta habilitar Just\-In\-Time sin permisos de administrador en estas condiciones, aparecerá el siguiente mensaje de error:  
  
 **Se denegó el acceso.  Pida al administrador que habilite la depuración Just\-In\-Time, o repare su instalación de Visual Studio.**  
  
## Vea también  
 [Depuración, Opciones \(Cuadro de diálogo\)](../debugger/debugging-options-dialog-box.md)   
 [Cómo: Especificar la configuración del depurador](../debugger/how-to-specify-debugger-settings.md)