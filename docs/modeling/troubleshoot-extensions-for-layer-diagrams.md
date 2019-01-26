---
title: Solucionar problemas de extensiones de diagramas de dependencia
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 01b8486c9ca0ffc62d338b9d9a46e50248182581
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028600"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Solucionar problemas de extensiones de diagramas de dependencia

En este tema se resuelven algunos problemas que pueden encontrarse al crear extensiones de modelo de capas.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Al presionar F5 para depurar una extensión, Mis comandos, controladores de gestos, extensiones de validación o propiedades personalizadas no aparecen en los diagramas de dependencia de la instancia Experimental de Visual Studio

1. Abra la solución de extensión en la instancia Experimental de Visual Studio y, en el **compilar** menú, haga clic en **recompilar solución**.

2. Presione **F5** o **CTRL+F5** para iniciar la instancia experimental de Visual Studio. Abra un diagrama de dependencia y probar la extensión.

   Continúe con el procedimiento siguiente si es necesario.

## <a name="an-old-version-of-my-extension-runs"></a>Se ejecuta una versión anterior de mi extensión.

1. Asegúrese de que no se está ejecutando ninguna instancia experimental de Visual Studio.

2. Elimine la siguiente carpeta: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [versión]

   > [!NOTE]
   > % LocalAppData % está normalmente *DriveName*: \Users\\*UserName*\AppData\Local.

   Continúe con el procedimiento siguiente si es necesario.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Aparece una versión anterior de mis resultados de validación o no se llama a mi método de validación.

1.  En la instancia experimental de Visual Studio, en el **compilar** menú, haga clic en **Limpiar solución**. Esto borra los resultados almacenados en memoria caché del análisis de validación anterior.

2.  Asegúrese de que las capas del modelo están asociadas a elementos de código y de que hay al menos un vínculo de dependencia en el modelo. La validación no se invoca si no hay nada que validar.

3.  Los puntos de interrupción normales podrían no funcionar en un método de validación, porque se ejecuta en un proceso independiente. Debe insertar una llamada a `System.Diagnostics.Debugger.Launch()` si desea reproducir paso a paso el método.

4.  En **source.extension.vsixmanifest** en el proyecto de validación de capas, asegúrese de que se ha agregado un **componente MEF** elemento y un **tipo de extensión personalizada** elemento bajo **Contenido**.

## <a name="see-also"></a>Vea también

- [Ampliación de diagramas de dependencia](../modeling/extend-layer-diagrams.md)
