---
title: Solucionar problemas de extensiones para diagramas de capas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c8ea8f4e6b102dd9bb4a84154096d5cef906eeab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250073"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Solucionar problemas de extensiones de diagramas de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se resuelven algunos problemas que pueden encontrarse al crear extensiones de modelo de capas.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Cuando presiono F5 para depurar una extensión, los comandos, controladores de gestos, extensiones de validación o propiedades personalizadas no aparecen en los diagramas de capas de la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1.  Abra la solución de extensión en la instancia Experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]y en el **compilar** menú, haga clic en **recompilar solución**.  
  
2.  Presione **F5** o **CTRL+F5** para iniciar la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Abra un diagrama de capas y pruebe la extensión.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Se ejecuta una versión anterior de mi extensión.  
  
1.  Asegúrese de que no se está ejecutando ninguna instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Elimine la siguiente carpeta: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [versión]  
  
    > [!NOTE]
    >  % LocalAppData % está normalmente *DriveName*: \Users\\*UserName*\AppData\Local.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Aparece una versión anterior de mis resultados de validación o no se llama a mi método de validación.  
  
1.  En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el **compilar** menú, haga clic en **Limpiar solución**. Esto borra los resultados almacenados en memoria caché del análisis de validación anterior.  
  
2.  Asegúrese de que las capas del modelo están asociadas a elementos de código y de que hay al menos un vínculo de dependencia en el modelo. La validación no se invoca si no hay nada que validar.  
  
3.  Los puntos de interrupción normales podrían no funcionar en un método de validación, porque se ejecuta en un proceso independiente. Debe insertar una llamada a `System.Diagnostics.Debugger.Launch()` si desea reproducir paso a paso el método.  
  
4.  En **source.extension.vsixmanifest** en el proyecto de validación de capas, asegúrese de que se ha agregado un **componente MEF** elemento y un **tipo de extensión personalizada** elemento bajo **Contenido**.  
  
## <a name="see-also"></a>Vea también  
 [Ampliar diagramas de capas](../modeling/extend-layer-diagrams.md)



