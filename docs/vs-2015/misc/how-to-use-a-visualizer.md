---
title: 'Cómo: usar un visualizador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
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
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778377"
---
# <a name="how-to-use-a-visualizer"></a>Cómo: Utilizar un visualizador
Puede utilizar un visualizador para mostrar el contenido de una variable o un objeto de manera significativa para el tipo de datos. Puede usar los visualizadores de **información sobre herramientas**, una ventana **inspección** , la ventana **automático** o la ventana **variables locales** .  
  
 Los visualizadores no se admiten en .NET Compact Framework.  
  
> [!NOTE]
> En las aplicaciones de la **tienda** , solo se admiten los visualizadores estándar de texto, HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
### <a name="to-open-a-visualizer"></a>Para abrir un visualizador  
  
1. Haga clic en el icono de lupa que aparece junto a un nombre de variable en **información sobre herramientas**, en una ventana **inspección** o en las ventanas **automático**, **variables locales**o **Inspección rápida** .  
  
     Se mostrará una lista de visualizadores.  
  
2. Haga clic en el visualizador que desee usar.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Para utilizar un visualizador para el código administrado durante la depuración remota  
  
- Copie el archivo DLL del visualizador en el equipo remoto antes de iniciar la sesión de depuración.  
  
     La ruta de acceso al archivo DLL debe ser la misma en el equipo remoto y en el equipo local. Esta ruta de acceso puede ser cualquiera de las siguientes ubicaciones:  
  
     *Ruta de acceso de instalación de Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     o bien  
  
     `My Documents\Visual Studio 2010\Visualizers`*Versión de Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Consulte también  
 [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Cómo: escribir un visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Ver valores de datos en sugerencias de datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)