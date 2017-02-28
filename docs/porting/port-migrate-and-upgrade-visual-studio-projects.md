---
title: Portar, migrar y actualizar proyectos de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4
ms.lasthandoff: 02/22/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar y actualizar proyectos de Visual Studio
Al pasar a una versión más reciente de Visual Studio, conviene saber si se debe modificar cualquiera de las soluciones, proyectos, archivos y otros activos que se crearon en versiones anteriores *antes de* ejecutarlos en versiones más recientes.

 Muchos activos ampliamente utilizados se comportan del mismo modo en las versiones Visual Studio 2017 RC y Visual Studio 2015. También se comportarán igual en versiones anteriores como Visual Studio 2013 y Visual Studio 2012.

 Por ejemplo, en Visual Studio 2017 RC puede abrir un proyecto creado en Visual Studio 2015 o Visual Studio 2013, cambiarlo y, a continuación, volver a abrirlo en Visual Studio 2017 RC; los cambios se conservan y el proyecto se comporta igual que en la versión anterior. Esto mismo sucede con muchos activos creados en Visual Studio 2012.  

 Si utiliza Visual Studio 2015 junto con Visual Studio 2013, Visual Studio 2012 o Visual Studio 2010 SP1, puede crear y modificar proyectos y archivos en cualquiera de estas versiones. Puede transferir proyectos y archivos entre las distintas versiones siempre y cuando no agregue características incompatibles con una de las versiones. (Para obtener más información sobre qué características son específicas de las versiones, consulte nuestras [Notas de la versión](https://www.visualstudio.com/vs/release-notes/)).

