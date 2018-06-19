---
title: Diseñador de flujo de trabajo - opciones de ejecución paso a paso de depuración (heredado)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969075"
---
# <a name="debug-stepping-options-legacy"></a>Depurar opciones de ejecución paso a paso (Heredado)

En este tema se describe cómo depurar aplicaciones de Windows Workflow Foundation (WF) que tengan actividades simultáneas en el Diseñador de flujo de trabajo de Windows heredado. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar una de las dos opciones siguientes para recorrer el código .

-   **Crear una bifurcación ejecución paso a paso.** Este modo de avance le permite recorrer y depurar una bifurcación determinada de una actividad compuesta, como el **ParallelActivity** o **ConditionalActivityGroup** actividad. Al utilizar esta opción para depurar, no advertirá que se produce un cambio de control como consecuencia de la ejecución simultánea de otras actividades en el flujo de trabajo. El depurador solo pasa a través de las actividades de la rama seleccionada actualmente aunque otras actividades del flujo de trabajo se puedan estar ejecutando de forma simultánea. Por ejemplo, de forma predeterminada, la bifurcación del extremo izquierdo en una **ParallelActivity** actividad y la primera actividad secundaria de un **ConditionedActivityGroup** actividad se utilizan para avanzar. Si el usuario está interesado en depurar cualquier otra rama o actividad secundaria, debe colocar un punto de interrupción explícito en esa rama o actividad secundaria. El avance continúa en esa bifurcación cuando se activa el punto de interrupción.

-   **La instancia de ejecución paso a paso.** Este modo de avance le permite pasar por y depurar actividades en el flujo de trabajo que se ejecutan concurrentemente. Con esta opción, observará que se produce un cambio de control al ejecutar actividades del flujo de trabajo simultáneamente.

De forma predeterminada, está seleccionada la opción de ejecución paso a paso por bifurcaciones y los usuarios pueden pasar de una opción a otra al depurar un flujo de trabajo heredado.

Debe seleccionar la opción de ejecución paso a paso por instancias cuando depure flujos de trabajo de máquina de estados heredados.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)
- [Cómo: Cambiar la opción de ejecución paso a paso de depuración (heredado)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)