---
title: 'Cómo: cambiar la opción de versión de depuración (heredado) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663436"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Cómo: Cambiar la opción de ejecución paso a paso de depuración (Heredado)
En este tema se describe cómo cambiar la opción de ejecución paso a paso de depuración para aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado con acciones simultáneas. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Al depurar actividades heredadas que tienen una ejecución simultánea, como **ParallelActivity** o **ConditionedActivityGroup**, puede usar una de estas dos opciones para recorrer el código.

 Siga estos pasos para cambiar la opción de ejecución paso a paso de depuración en el proyecto de flujo de trabajo heredado.

## <a name="procedures"></a>Procedimientos

#### <a name="to-change-the-debug-stepping-option"></a>Para cambiar la opción de ejecución paso a paso de depuración

1. Inicie Visual Studio.

2. Abra un proyecto de flujo de trabajo heredado existente o cree un nuevo proyecto que use actividades simultáneas y que tenga como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

3. En el menú **flujo de trabajo** del heredado [!INCLUDE[wfd2](../includes/wfd2-md.md)] , elija **depurar**y, a continuación, elija **Opciones de ejecución paso a paso**.

4. Seleccione **instancia** o **rama**.

## <a name="see-also"></a>Consulte también
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md) [Opciones de versión de depuración (heredado)](../workflow-designer/debug-stepping-options-legacy.md)