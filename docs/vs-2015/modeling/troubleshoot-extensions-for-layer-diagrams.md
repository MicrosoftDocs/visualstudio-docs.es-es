---
title: Solucionar problemas de extensiones para diagramas de capas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658477"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Solucionar problemas de extensiones de diagramas de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se resuelven algunos problemas que pueden encontrarse al crear extensiones de modelo de capas.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-vsprvs"></a>Cuando presiono F5 para depurar una extensión, los comandos, controladores de gestos, extensiones de validación o propiedades personalizadas no aparecen en los diagramas de capas de la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Abra la solución de extensión en la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y, en el menú **compilar** , haga clic en **recompilar solución**.

2. Presione **F5** o **Ctrl + F5** para iniciar la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Abra un diagrama de capas y pruebe la extensión.

   Continúe con el procedimiento siguiente si es necesario.

#### <a name="an-old-version-of-my-extension-runs"></a>Se ejecuta una versión anterior de mi extensión.

1. Asegúrese de que no se está ejecutando ninguna instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Elimine la siguiente carpeta:%LocalAppData%\Microsoft\VisualStudio \\ [versión] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData *% suele ser*el nombre de \\ *usuario*\AppData\Local.

   Continúe con el procedimiento siguiente si es necesario.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Aparece una versión anterior de mis resultados de validación o no se llama a mi método de validación.

1. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , en el menú **compilar** , haga clic en **limpiar solución**. Esto borra los resultados almacenados en memoria caché del análisis de validación anterior.

2. Asegúrese de que las capas del modelo están asociadas a elementos de código y de que hay al menos un vínculo de dependencia en el modelo. La validación no se invoca si no hay nada que validar.

3. Los puntos de interrupción normales podrían no funcionar en un método de validación, porque se ejecuta en un proceso independiente. Debe insertar una llamada a `System.Diagnostics.Debugger.Launch()` si desea reproducir paso a paso el método.

4. En **source. Extension. vsixmanifest** en el proyecto de validación de capas, asegúrese de que ha agregado un elemento de **componente de MEF** y un elemento de **tipo de extensión personalizado** en **contenido**.

## <a name="see-also"></a>Consulte también
 [Ampliar diagramas de capas](../modeling/extend-layer-diagrams.md)
