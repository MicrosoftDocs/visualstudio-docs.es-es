---
title: Solucionar problemas de extensiones para diagramas de dependencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Solucionar problemas de extensiones para diagramas de dependencia
En este tema se resuelven algunos problemas que pueden encontrarse al crear extensiones de modelo de capas.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Al presionar F5 para depurar una extensión, mi comandos, controladores de gestos, extensiones de validación o las propiedades personalizadas no aparecen en los diagramas de dependencia de la instancia Experimental de[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Abra la solución de extensión en la instancia Experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]y en el **crear** menú, haga clic en **volver a generar solución**.  
  
2.  Presione **F5** o **CTRL+F5** para iniciar la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Abra un diagrama de dependencia y probar la extensión.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Se ejecuta una versión anterior de mi extensión.  
  
1.  Asegúrese de que no se está ejecutando ninguna instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Elimine la siguiente carpeta: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [versión]  
  
    > [!NOTE]
    >  % LocalAppData % suele *DriveName*: \Users\\*nombre de usuario*\AppData\Local.  
  
 Continúe con el procedimiento siguiente si es necesario.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Aparece una versión anterior de mis resultados de validación o no se llama a mi método de validación.  
  
1.  En la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en la **crear** menú, haga clic en **Limpiar solución**. Esto borra los resultados almacenados en memoria caché del análisis de validación anterior.  
  
2.  Asegúrese de que las capas del modelo están asociadas a elementos de código y de que hay al menos un vínculo de dependencia en el modelo. La validación no se invoca si no hay nada que validar.  
  
3.  Los puntos de interrupción normales podrían no funcionar en un método de validación, porque se ejecuta en un proceso independiente. Debe insertar una llamada a `System.Diagnostics.Debugger.Launch()` si desea reproducir paso a paso el método.  
  
4.  En **source.extension.vsixmanifest** en su proyecto de validación de capas, asegúrese de que ha agregado un **componente MEF** elemento y un **tipo de extensión personalizada** elementos en **contenido**.  
  
## <a name="see-also"></a>Vea también  
 [Ampliar diagramas de dependencia](../modeling/extend-layer-diagrams.md)

