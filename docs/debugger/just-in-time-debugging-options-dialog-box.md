---
title: Just-In-Time, depuración, cuadro de diálogo Opciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7be7dacbe7b3b89b8bdc09515c23d7597e7e55e5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480894"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Depuración, Opciones (Cuadro de diálogo)
Para tener acceso a la **Just-In-Time** página, vaya a la **herramientas** menú y haga clic en **opciones**. En el **opciones** cuadro de diálogo, expanda el **depuración** nodo y seleccione **Just-In-Time**. Esta página permite habilitar la depuración Just-In-Time para el código administrado, código nativo y scripts. Para obtener más información, consulte [depuración Just](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Puede habilitar la depuración Just-In-Time para estos tipos de programas:  
  
-   Administrado  
  
-   Nativo  
  
-   Script  
  
 La depuración Just-In-Time es una técnica para depurar un programa iniciado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Puede ejecutar un sistema creado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fuera del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si ha habilitado la depuración Just-In-Time, un bloqueo mostrará un cuadro de diálogo en el que se le preguntará si desea depurar.  
  
## <a name="associated-warnings"></a>Advertencias asociadas  
 Cuando visite esta página de la **opciones** cuadro de diálogo, verá un mensaje de advertencia similar al siguiente:  
  
 **Otro depurador se ha registrado como Just-In-Time depurador. Para reparar, habilite Just-In-Time depurar o ejecutar la reparación de Visual Studio.**  
  
 Este mensaje aparece si hay otro depurador, posiblemente una versión anterior del depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definido como el depurador Just-In-Time.  
  
 Otro mensaje que podría ver es el siguiente:  
  
 **Just-In-Time depuración registro errores detectados. Para reparar, habilite Just-In-Time depurar o ejecutar la reparación de Visual Studio.**  
  
 Si ve cualquiera de estas advertencias, la depuración Just-In-Time [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] requiere privilegios de administrador hasta que corrija el problema. Si intenta habilitar Just-In-Time sin permisos de administrador en estas condiciones, aparecerá el siguiente mensaje de error:  
  
 **Se denegó el acceso. Disponer de un administrador de depuración de habilitar Just-In-Time o reparar la instalación de Visual Studio.**  
  
## <a name="see-also"></a>Vea también  
 [Depuración, cuadro de diálogo Opciones](../debugger/debugging-options-dialog-box.md)   
 [Cómo: Especificar la configuración del depurador](../debugger/how-to-specify-debugger-settings.md)