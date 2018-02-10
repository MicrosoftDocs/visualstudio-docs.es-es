---
title: Solucionar problemas de extensiones para diagramas de dependencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 21a14ed32bb1b63e2363736e438139479ff5bf60
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Solucionar problemas de extensiones para diagramas de dependencia
En este tema se resuelven algunos problemas que pueden encontrarse al crear extensiones de modelo de capas.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Al presionar F5 para depurar una extensión, mi comandos, controladores de gestos, extensiones de validación o las propiedades personalizadas no aparecen en los diagramas de dependencia de la instancia Experimental de[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Abra la solución de extensión en la instancia Experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]y en el **generar** menú, haga clic en **volver a generar solución**.  
  
2.  Presione **F5** o **CTRL+F5** para iniciar la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Abra un diagrama de dependencia y probar la extensión.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Se ejecuta una versión anterior de mi extensión.  
  
1.  Asegúrese de que no se está ejecutando ninguna instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Elimine la carpeta siguiente: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [versión]  
  
    > [!NOTE]
    >  Suele ser % LocalAppData % *DriveName*: \Users\\*nombre de usuario*\AppData\Local.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Aparece una versión anterior de mis resultados de validación o no se llama a mi método de validación.  
  
1.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en la **generar** menú, haga clic en **Limpiar solución**. Esto borra los resultados almacenados en memoria caché del análisis de validación anterior.  
  
2.  Asegúrese de que las capas del modelo están asociadas a elementos de código y de que hay al menos un vínculo de dependencia en el modelo. La validación no se invoca si no hay nada que validar.  
  
3.  Los puntos de interrupción normales podrían no funcionar en un método de validación, porque se ejecuta en un proceso independiente. Debe insertar una llamada a `System.Diagnostics.Debugger.Launch()` si desea reproducir paso a paso el método.  
  
4.  En **source.extension.vsixmanifest** en su proyecto de validación de capas, asegúrese de que ha agregado un **componente MEF** elemento y un **tipo de extensión personalizada** elemento bajo **Contenido**.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de diagramas de dependencia](../modeling/extend-layer-diagrams.md)
