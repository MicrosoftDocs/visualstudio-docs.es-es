---
title: 'Cómo: utilizar un visualizador | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.author: susanno
manager: douge
ms.openlocfilehash: cc158e0d84db56bc26262d60acd0fb8e92e47188
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578450"
---
# <a name="how-to-use-a-visualizer"></a>Cómo: Utilizar un visualizador
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
  
     O bien  
  
     `My Documents\Visual Studio 2010\Visualizers` *Versión de Visual Studio* `\Visualizers`  
  
## <a name="see-also"></a>Vea también  
 [Crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Cómo: instalar un visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Cómo: escribir un visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Ver valores de datos en sugerencias de datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)