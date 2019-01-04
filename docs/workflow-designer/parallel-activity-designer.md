---
title: Diseñador de flujo de trabajo - Diseñador de actividad Parallel
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ad0d0d44c18c17dd1602c51954a7c529b84d114
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843611"
---
# <a name="parallel-activity-designer"></a>Diseñador de actividades Parallel

La actividad de la clase <xref:System.Activities.Statements.Parallel> ejecuta una colección de actividades secundarias simultáneamente.

## <a name="the-parallel-activity"></a>La actividad de la clase Parallel

La actividad de la clase <xref:System.Activities.Statements.Parallel> almacena sus actividades secundarias en una colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A>. Use la actividad de la clase <xref:System.Activities.Statements.Parallel> en vez de la actividad de la clase <xref:System.Activities.Statements.Sequence> si alguna de las actividades secundarias se puede quedar inactiva.

El <xref:System.Activities.Statements.Parallel> actividad tiene un <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> propiedad que contiene un usuario especifica la expresión de Visual Basic. La actividad <xref:System.Activities.Statements.Parallel> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad se completa sin ejecutar las demás ramas. Si el <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> no se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad se completa cuando se hayan completado todas sus actividades secundarias.

### <a name="using-the-parallel-activity-designer"></a>Usar el diseñador de actividad Parallel

Acceso a la **paralelo** Diseñador de actividad en el **flujo de Control** categoría de la **cuadro de herramientas**.

El **paralelo** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo siempre que sea, por ejemplo, los diseñadores de actividad normalmente se colocan dentro de un **Secuencia** Diseñador de actividad. Después de colocarlo en el Diseñador de flujo de trabajo, crea un <xref:System.Activities.Statements.Parallel> actividad, que de forma predeterminada, contiene un <xref:System.Activities.Activity.DisplayName%2A> de **paralelo**

Para agregar una actividad para el <xref:System.Activities.Statements.Parallel.Branches%2A> colección de la actividad parallel, arrastre algún otro diseñador de actividad desde el **cuadro de herramientas** y colóquelo en el triángulo dentro de la **paralelo** Diseñador de actividad. Los triángulos rodean las actividades contenidas en las bifurcaciones. Las actividades adicionales se pueden agregar repitiendo este procedimiento. Las actividades se pueden reordenar arrastrándolos y colocándolos en la **paralelo** Diseñador de actividad.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Parallel en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las propiedades de la actividad Parallel y se describe cómo se usan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **paralelo**. El valor se puede editar, opcionalmente, en el **propiedades** cuadrícula o directamente en el encabezado del Diseñador de actividad.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la colección de actividades secundarias que se van a ejecutar.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Se evalúa cuando se completa una bifurcación. Si se evalúa como **True**, a continuación, programados bifurcaciones pendientes se cancelan. Si esta propiedad no se ha establecido o se evalúa como **False**, la actividad se completa cuando se hayan completado todas sus actividades secundarias. El valor predeterminado es **null**.|

## <a name="see-also"></a>Vea también

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)