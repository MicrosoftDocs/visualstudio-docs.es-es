---
title: Depurar opciones de ejecución paso a paso (heredado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b7dfaa4fb659418c26d5aa0144fac4188ef4b16b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899388"
---
# <a name="debug-stepping-options-legacy"></a>Depurar opciones de ejecución paso a paso (Heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] con actividades simultáneas en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar una de las dos opciones siguientes para recorrer el código .  
  
- **Ejecución paso por bifurcaciones.** Este modo de avance le permite recorrer y depurar una bifurcación determinada de una actividad compuesta, como el **ParallelActivity** o **ConditionalActivityGroup** actividad. Al utilizar esta opción para depurar, no advertirá que se produce un cambio de control como consecuencia de la ejecución simultánea de otras actividades en el flujo de trabajo. El depurador solo pasa a través de las actividades de la rama seleccionada actualmente aunque otras actividades del flujo de trabajo se puedan estar ejecutando de forma simultánea. Por ejemplo, de forma predeterminada, la rama del extremo izquierdo en un **ParallelActivity** actividad y la primera actividad secundaria de un **ConditionedActivityGroup** actividad se usan para la ejecución paso a paso. Si el usuario está interesado en depurar cualquier otra rama o actividad secundaria, debe colocar un punto de interrupción explícito en esa rama o actividad secundaria. El avance continúa en esa bifurcación cuando se activa el punto de interrupción.  
  
- **La instancia de ejecución paso a paso.** Este modo de avance le permite pasar por y depurar actividades en el flujo de trabajo que se ejecutan concurrentemente. Con esta opción, observará que se produce un cambio de control al ejecutar actividades del flujo de trabajo simultáneamente.  
  
  De forma predeterminada, está seleccionada la opción de ejecución paso a paso por bifurcaciones y los usuarios pueden pasar de una opción a otra al depurar un flujo de trabajo heredado.  
  
  Debe seleccionar la opción de ejecución paso a paso por instancias cuando depure flujos de trabajo de máquina de estados heredados.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)   
 [Cómo: Cambiar la opción de ejecución paso a paso de depuración (heredado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)