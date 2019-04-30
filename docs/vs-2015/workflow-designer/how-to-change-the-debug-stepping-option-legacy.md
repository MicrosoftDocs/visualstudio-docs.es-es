---
title: Procedimiento Cambiar la opción de ejecución paso a paso de depuración (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 505f876b9c7943c8b039b74459552b77ce539477
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954458"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procedimiento Cambiar la opción de ejecución paso a paso de depuración (heredado)
En este tema se describe cómo cambiar la opción de ejecución paso a paso de depuración para aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado con acciones simultáneas. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar uno de dos opciones para recorrer el código.  
  
 Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-change-the-debug-stepping-option"></a>Para cambiar la opción de ejecución paso a paso de depuración  
  
1. Inicie Visual Studio.  
  
2. Abra un proyecto de flujo de trabajo heredado existente o cree un nuevo proyecto que use actividades simultáneas y que tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
3. En el **flujo de trabajo** menú heredado [!INCLUDE[wfd2](../includes/wfd2-md.md)], apunte a **depurar**y, a continuación, elija **opciones de ejecución paso a paso**.  
  
4. Seleccione **instancia** o **rama**.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)   
 [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)