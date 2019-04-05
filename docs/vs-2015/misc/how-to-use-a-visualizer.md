---
title: Filtrar Utilizar un visualizador | Documentos de Microsoft
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
ms.openlocfilehash: 7ec7527e51175b82d06a35ad7a6bc26856acf5dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995418"
---
# <a name="how-to-use-a-visualizer"></a>Filtrar Utilizar un visualizador
Puede utilizar un visualizador para mostrar el contenido de una variable o un objeto de manera significativa para el tipo de datos. Puede usar los visualizadores de **DataTips**, un **inspección** ventana, el **automático** ventana, o la **variables locales** ventana.  
  
 Los visualizadores no se admiten en .NET Compact Framework.  
  
> [!NOTE]
>  En **Store** aplicaciones, sólo el texto estándar, se admiten los visualizadores HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).  
  
### <a name="to-open-a-visualizer"></a>Para abrir un visualizador  
  
1.  Haga clic en el icono de lupa que aparece junto al nombre de variable en **DataTips**, un **inspección** ventana, o en el **automático**, **variables locales**, o **Inspección rápida** ventana.  
  
     Se mostrará una lista de visualizadores.  
  
2.  Haga clic en el visualizador que desee usar.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Para utilizar un visualizador para el código administrado durante la depuración remota  
  
-   Copie el archivo DLL del visualizador en el equipo remoto antes de iniciar la sesión de depuración.  
  
     La ruta de acceso al archivo DLL debe ser la misma en el equipo remoto y en el equipo local. Esta ruta de acceso puede ser cualquiera de las siguientes ubicaciones:  
  
     *Ruta de instalación de Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     -o bien-  
  
     `My Documents\Visual Studio 2010\Visualizers` *Versión de Visual Studio* `\Visualizers`  
  
## <a name="see-also"></a>Vea también  
 [Creación de visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: Instalación de un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Cómo: Escritura de un visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Ver valores de datos en sugerencias de datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)