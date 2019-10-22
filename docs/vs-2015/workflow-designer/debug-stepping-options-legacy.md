---
title: Opciones de paso de depuración (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656876"
---
# <a name="debug-stepping-options-legacy"></a>Depurar opciones de ejecución paso a paso (Heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] con actividades simultáneas en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Al depurar actividades heredadas que tienen una ejecución simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar una de las dos opciones siguientes para recorrer el código.

- **Ejecución paso a paso.** Este modo de ejecución paso a paso le permite recorrer y depurar una bifurcación determinada de una actividad compuesta, como la actividad **ParallelActivity** o **ConditionalActivityGroup** . Al utilizar esta opción para depurar, no advertirá que se produce un cambio de control como consecuencia de la ejecución simultánea de otras actividades en el flujo de trabajo. El depurador solo pasa a través de las actividades de la bifurcación seleccionada actualmente aunque otras actividades del flujo de trabajo se puedan estar ejecutando de forma simultánea. Por ejemplo, de forma predeterminada, la bifurcación situada más a la izquierda en una actividad **ParallelActivity** y la primera actividad secundaria de una actividad **ConditionedActivityGroup** se usan para la ejecución paso a paso. Si el usuario está interesado en depurar cualquier otra rama o actividad secundaria, debe colocar un punto de interrupción explícito en esa rama o actividad secundaria. El avance continúa en esa bifurcación cuando se activa el punto de interrupción.

- **Ejecución paso a paso de instancia.** Este modo de avance le permite pasar por y depurar actividades en el flujo de trabajo que se ejecutan concurrentemente. Con esta opción, observará que se produce un cambio de control al ejecutar actividades del flujo de trabajo simultáneamente.

  De forma predeterminada, está seleccionada la opción de ejecución paso a paso por bifurcaciones y los usuarios pueden pasar de una opción a otra al depurar un flujo de trabajo heredado.

  Debe seleccionar la opción de ejecución paso a paso por instancias cuando depure flujos de trabajo de máquina de estados heredados.

## <a name="see-also"></a>Vea también
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md) [Cómo: cambiar la opción de versión de depuración (heredado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)