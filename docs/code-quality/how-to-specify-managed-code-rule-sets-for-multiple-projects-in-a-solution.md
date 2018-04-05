---
title: "Cómo: especificar conjuntos de reglas de código administrado para varios proyectos en una solución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Cómo: Especificar conjuntos de reglas de código administrado para varios proyectos de una solución

De forma predeterminada, todos los proyectos administrados de una solución se asignan el análisis de código reglas mínimas recomendadas de Microsoft *conjunto de reglas*. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo de propiedades de la solución.

> [!NOTE]
> De forma predeterminada, el análisis de código del proyecto no se ejecuta como un paso de compilación. Para habilitar el análisis de código como un paso de compilación, consulte [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

1. Abra la solución en Visual Studio.

2. En el **analizar** menú, haga clic en **configurar análisis de código para la solución**.

3. Si es necesario, expanda **propiedades comunes**y, a continuación, haga clic en **configuración de análisis de código**.

4. Puede especificar un conjunto de reglas para uno o varios proyectos.

    - Para especificar un conjunto de reglas para un proyecto individual, haga clic en el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla CTRL y haga clic en los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga presionada la tecla MAYÚS y haga clic en la lista de proyectos.

5. Haga clic en el **conjunto de reglas** campo de un proyecto y, a continuación, haga clic en el nombre de la regla que desea aplicar.