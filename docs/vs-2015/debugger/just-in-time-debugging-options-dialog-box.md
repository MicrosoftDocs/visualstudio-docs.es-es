---
title: Just-In-Time, depuración, cuadro de diálogo Opciones | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201104"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Depuración, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener acceso a la página **Just-In-Time**, vaya al menú **Herramientas** y haga clic en **Opciones**. En el cuadro de diálogo **Opciones**, expanda el nodo **Depuración** y seleccione **Just-In-Time**. Esta página permite habilitar la depuración Just-In-Time para el código administrado, código nativo y scripts. Para obtener más información, vea [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Puede habilitar la depuración Just-In-Time para estos tipos de programas:  
  
- Administrado  
  
- Nativo  
  
- Script  
  
  La depuración Just-In-Time es una técnica para depurar un programa iniciado fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Puede ejecutar un sistema creado en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fuera del entorno de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si ha habilitado la depuración Just-In-Time, un bloqueo mostrará un cuadro de diálogo en el que se le preguntará si desea depurar.  
  
## <a name="associated-warnings"></a>Advertencias asociadas  
 Cuando visite esta página del cuadro de diálogo **Opciones**, es posible que aparezca un mensaje de advertencia como este:  
  
 **Otro depurador se ha registrado como el depurador Just-In-Time. Para reparar, habilite la depuración Just-In-Time o ejecute la reparación de Visual Studio.**  
  
 Este mensaje aparece si hay otro depurador, posiblemente una versión anterior del depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], definido como el depurador Just-In-Time.  
  
 Otro mensaje que podría ver es el siguiente:  
  
 **Errores de registro de la depuración Just-In-Time. Para reparar, habilite la depuración Just-In-Time o ejecute la reparación de Visual Studio.**  
  
 Si aparece cualquiera de estas advertencias, la depuración Just-In-Time con [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] requiere privilegios de administrador hasta que se corrija el problema. Si intenta habilitar Just-In-Time sin permisos de administrador en estas condiciones, aparecerá el siguiente mensaje de error:  
  
 **Acceso denegado. Pida al administrador que habilite la depuración Just-In-Time, o repare su instalación de Visual Studio.**  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo Depuración, Opciones](../debugger/debugging-options-dialog-box.md)   
 [Procedimientos: Especificación de la configuración del depurador](../debugger/how-to-specify-debugger-settings.md)
