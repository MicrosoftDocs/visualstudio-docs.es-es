---
title: Just-In-Time, depuración, cuadro de diálogo Opciones | Documentos de Microsoft
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
manager: ghogen
ms.openlocfilehash: 06fdd9d12003053ea6d992aa1d7d0fe9ed7144d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788139"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Depuración, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para tener acceso a la **Just-In-Time** página, vaya a la **herramientas** menú y haga clic en **opciones**. En el **opciones** cuadro de diálogo, expanda el **depuración** nodo y seleccione **Just-In-Time**. Esta página permite habilitar la depuración Just-In-Time para el código administrado, código nativo y scripts. Para obtener más información, consulte [depuración Just](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Puede habilitar la depuración Just-In-Time para estos tipos de programas:  
  
- Administrado  
  
- Nativo  
  
- Script  
  
  La depuración Just-In-Time es una técnica para depurar un programa iniciado fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Puede ejecutar un sistema creado en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fuera del entorno de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si ha habilitado la depuración Just-In-Time, un bloqueo mostrará un cuadro de diálogo en el que se le preguntará si desea depurar.  
  
## <a name="associated-warnings"></a>Advertencias asociadas  
 Cuando visite esta página de la **opciones** cuadro de diálogo, es posible que vea un mensaje de advertencia como este:  
  
 **Otro depurador se ha registrado como Just-In-Time depurador. Para reparar, habilite Just-In-Time depurar o ejecutar la reparación de Visual Studio.**  
  
 Este mensaje aparece si hay otro depurador, posiblemente una versión anterior del depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], definido como el depurador Just-In-Time.  
  
 Otro mensaje que podría ver es el siguiente:  
  
 **Just-In-Time depuración errores de registro. Para reparar, habilite Just-In-Time depurar o ejecutar la reparación de Visual Studio.**  
  
 Si aparece cualquiera de estas advertencias, con la depuración Just-In-Time [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] requiere privilegios de administrador hasta que corrija el problema. Si intenta habilitar Just-In-Time sin permisos de administrador en estas condiciones, aparecerá el siguiente mensaje de error:  
  
 **Acceso denegado. Tiene un administrador de depuración de habilitar Just-In-Time o repare la instalación de Visual Studio.**  
  
## <a name="see-also"></a>Vea también  
 [Depuración, cuadro de diálogo Opciones](../debugger/debugging-options-dialog-box.md)   
 [Cómo: Especificar la configuración del depurador](../debugger/how-to-specify-debugger-settings.md)



