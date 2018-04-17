---
title: 'Cómo: cambiar la opción de ejecución paso a paso de depuración (heredado) | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aedb8e738dc2e6ca2b066dd9a2cd42e332bbd8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Cómo: Cambiar la opción de ejecución paso a paso de depuración (Heredado)
Este tema describe cómo cambiar la opción de ejecución paso a paso de depuración para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicaciones en el Diseñador de flujo de trabajo heredado de Windows que tengan acciones simultáneas. Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar uno de dos opciones para recorrer el código.

 Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.

## <a name="procedures"></a>Procedimientos

#### <a name="to-change-the-debug-stepping-option"></a>Para cambiar la opción de ejecución paso a paso de depuración

1.  Inicie Visual Studio.

2.  Abra un proyecto de flujo de trabajo heredado existente o cree un nuevo proyecto que use actividades simultáneas y que tenga como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

3.  En el **flujo de trabajo** menú heredado [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], seleccione **depurar**y, a continuación, seleccione **opciones de ejecución paso a paso**.

4.  Seleccione **instancia** o **bifurcación**.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)
- [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)