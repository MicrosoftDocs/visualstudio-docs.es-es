---
title: 'Diseñador de flujo de trabajo: Cómo: cambiar la opción de ejecución paso a paso de depuración (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 31047cedd4e8772b9ebab4ef238a8fe32bc07663
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971988"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Cómo: Cambiar la opción de ejecución paso a paso de depuración (Heredado)

En este tema se describe cómo cambiar la opción para las aplicaciones de Windows Workflow Foundation (WF) en el Diseñador de flujo de trabajo heredado de Windows que tienen acciones simultáneas del recorrido de depuración. Use el Diseñador de flujo de trabajo heredado cuando deba tener como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

Cuando esté depurando actividades heredadas cuya ejecución sea simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar uno de dos opciones para recorrer el código.

Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.

## <a name="procedures"></a>Procedimientos

### <a name="to-change-the-debug-stepping-option"></a>Para cambiar la opción de ejecución paso a paso de depuración

1.  Inicie Visual Studio.

2.  Abra un proyecto de flujo de trabajo heredado existente o crear un nuevo proyecto que utiliza actividades simultáneas y que tiene como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

3.  En el **flujo de trabajo** menú en el Diseñador de flujo de trabajo heredado, apunte a **depurar**y, a continuación, seleccione **opciones de ejecución paso a paso**.

4.  Seleccione **instancia** o **bifurcación**.

## <a name="see-also"></a>Vea también

- [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)
- [Depurar opciones de ejecución paso a paso (heredado)](../workflow-designer/debug-stepping-options-legacy.md)