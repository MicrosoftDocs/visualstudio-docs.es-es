---
title: 'Cómo: especificar conjuntos de reglas de código administrado para varios proyectos de una solución | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656420"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Cómo: Especificar conjuntos de reglas de código administrado para varios proyectos de una solución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, todos los proyectos administrados de una solución tienen asignado el *conjunto de reglas*de análisis de código reglas mínimas recomendadas de Microsoft. Puede cambiar los conjuntos de reglas que se asignan a los proyectos de una solución en el cuadro de diálogo de propiedades de la solución.

> [!NOTE]
> De forma predeterminada, el análisis de código del proyecto no se ejecuta como un paso de compilación. Para habilitar el análisis de código como paso de compilación, vea [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Para especificar un conjunto de reglas para varios proyectos de una solución de código administrado

1. En [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. En [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)], abra la solución.

2. En el menú **analizar** , haga clic en **configurar análisis de código para la solución**.

3. Si es necesario, expanda **propiedades comunes**y, a continuación, haga clic en **configuración de análisis de código**.

4. Puede especificar un conjunto de reglas para uno o varios proyectos.

    - Para especificar un conjunto de reglas para un proyecto individual, haga clic en el nombre del proyecto.

    - Para especificar un conjunto de reglas para varios proyectos, mantenga presionada la tecla CTRL y haga clic en los nombres de proyecto.

    - Para especificar todos los proyectos de la solución, mantenga presionada la tecla MAYÚS y haga clic en la lista de proyectos.

5. Haga clic en el campo **conjunto de reglas** de un proyecto y, a continuación, haga clic en el nombre del conjunto de reglas que desea aplicar.
