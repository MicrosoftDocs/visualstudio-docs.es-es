---
title: Just-In-Time, Depuración, Opciones (cuadro de diálogo) | Microsoft Docs
description: La depuración Just-in-Time permite depurar programas que se inician fuera de Visual Studio. Obtenga información sobre cómo habilitar la depuración Just-In-Time para varios tipos de programas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b346cfdae8671f8f647d41065d5793184fefd3fb
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903875"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-In-Time, Depuración, Opciones (cuadro de diálogo)
Para obtener acceso a la página **Just-In-Time**, vaya al menú **Herramientas** y haga clic en **Opciones**. En el cuadro de diálogo **Opciones**, expanda el nodo **Depuración** y seleccione **Just-In-Time**. Esta página permite habilitar la depuración Just-In-Time para el código administrado, código nativo y scripts. Para obtener más información, vea [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md).

 Puede habilitar la depuración Just-In-Time para estos tipos de programas:

- Administrado

- Nativo

- Script

  La depuración Just-In-Time es una técnica para depurar un programa iniciado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Puede ejecutar un sistema creado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fuera del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si ha habilitado la depuración Just-In-Time, un bloqueo mostrará un cuadro de diálogo en el que se le preguntará si desea depurar.

## <a name="associated-warnings"></a>Advertencias asociadas
 Cuando visite esta página del cuadro de diálogo **Opciones**, es posible que aparezca un mensaje de advertencia como este:

 **Otro depurador se ha registrado como el depurador Just-In-Time. Para reparar, habilite la depuración Just-In-Time o ejecute la reparación de Visual Studio.**

 Este mensaje aparece si hay otro depurador, posiblemente una versión anterior del depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definido como el depurador Just-In-Time.

 Otro mensaje que podría ver es el siguiente:

 **Errores de registro de la depuración Just-In-Time. Para reparar, habilite la depuración Just-In-Time o ejecute la reparación de Visual Studio.**

 Si aparece cualquiera de estas advertencias, la depuración Just-In-Time con [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] requiere privilegios de administrador hasta que se corrija el problema. Si intenta habilitar Just-In-Time sin permisos de administrador en estas condiciones, aparecerá el siguiente mensaje de error:

 **Acceso denegado. Pida al administrador que habilite la depuración Just-In-Time, o repare su instalación de Visual Studio.**

## <a name="see-also"></a>Vea también
- [Depuración, Cuadro de diálogo Opciones](../debugger/debugging-options-dialog-box.md)
- [Cómo: Especificación de la configuración del depurador](../debugger/how-to-specify-debugger-settings.md)