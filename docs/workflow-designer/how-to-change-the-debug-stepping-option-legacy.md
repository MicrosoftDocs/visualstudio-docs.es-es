---
title: "Cómo: cambiar la opción de ejecución paso a paso de depuración (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: bc92b5babe53b249fc66d93adbc0d69e6f7cf0e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Cómo: Cambiar la opción de ejecución paso a paso de depuración (Heredado)
En este tema se describe cómo cambiar la opción de ejecución paso a paso de depuración para aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado con acciones simultáneas. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar uno de dos opciones para recorrer el código.  
  
 Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-change-the-debug-stepping-option"></a>Para cambiar la opción de ejecución paso a paso de depuración  
  
1.  Inicie Visual Studio.  
  
2.  Abra un proyecto de flujo de trabajo heredado existente o cree un nuevo proyecto que use actividades simultáneas y que tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  En el **flujo de trabajo** menú heredado [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], seleccione **depurar**y, a continuación, seleccione **opciones de ejecución paso a paso**.  
  
4.  Seleccione **instancia** o **bifurcación**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar flujos de trabajo heredado](../workflow-designer/debugging-legacy-workflows.md)   
 [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)