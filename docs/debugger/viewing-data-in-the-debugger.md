---
title: Crear vistas personalizadas de datos en el depurador | Documentos de Microsoft
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e8f008ba3cde911ed5c21f281d30fda2a77bf824
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Crear vistas personalizadas de datos en el depurador de Visual Studio
El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona una gran variedad de herramientas para inspeccionar y modificar el estado de los programas. La mayoría de estas herramientas sólo funcionan en el modo de interrupción.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Crear vistas personalizadas de datos en ventanas de variables y la información sobre datos
 Muchos de los [ventanas del depurador](../debugger/debugger-windows.md), como el **automático** y **inspección** windows, permiten inspeccionar las variables durante la depuración. Puede personalizar la presentación de los tipos nativos y los objetos administrados en las ventanas de variables del depurador y en [información sobre datos](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Esto puede resultar útil para mostrar los tipos creados en sus propias aplicaciones. Para obtener más información, consulte [crear vistas personalizadas de objetos nativos](../debugger/create-custom-views-of-native-objects.md) y [crear vistas personalizadas de los objetos administrados](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Crear los visualizadores personalizados  
 Los visualizadores permiten ver el contenido de un objeto o variable de forma significativa. En el depurador de Visual Studio, un visualizador hace referencia a las diferentes ventanas que se pueden abrir mediante el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador"). Por ejemplo, puede utilizar el visualizador HTML para ver una cadena HTML tal como se interpretaría y se mostraría en un explorador. Puede tener acceso a los visualizadores desde información sobre datos, la ventana **Inspección** , la ventana **Automático** , la ventana **Variables locales** o el cuadro de diálogo **Inspección rápida** . Para obtener más información, consulte [crear visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Ventana Comandos](../ide/reference/command-window.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)