---
title: Diseñador de actividades en paralelo | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c3f24af736dfd3762de7942ba1f52442dfd20c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-activity-designer"></a>Diseñador de actividades Parallel
La actividad de la clase <xref:System.Activities.Statements.Parallel> ejecuta una colección de actividades secundarias simultáneamente.

## <a name="the-parallel-activity"></a>La actividad de la clase Parallel
 La actividad de la clase <xref:System.Activities.Statements.Parallel> almacena sus actividades secundarias en una colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A>. Use la actividad de la clase <xref:System.Activities.Statements.Parallel> en vez de la actividad de la clase <xref:System.Activities.Statements.Sequence> si alguna de las actividades secundarias se puede quedar inactiva.

 La actividad <xref:System.Activities.Statements.Parallel> tiene una propiedad <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contiene a una expresión [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] especificada por el usuario. La actividad <xref:System.Activities.Statements.Parallel> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad completa sin ejecutar las otras bifurcaciones. Si el <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> no se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad se completa cuando se hayan completado todas sus actividades secundarias.

### <a name="using-the-parallel-activity-designer"></a>Usar el diseñador de actividad Parallel
 El **paralelo** Diseñador de actividad puede encontrarse en el **flujo de Control** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **paralelo** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta donde los diseñadores de actividades se coloquen normalmente, por ejemplo, dentro de un **Secuencia** Diseñador de actividad. Después de colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], crea un <xref:System.Activities.Statements.Parallel> actividad, que, de forma predeterminada, contiene un <xref:System.Activities.Activity.DisplayName%2A> de **paralelas**

 Para agregar una actividad a la <xref:System.Activities.Statements.Parallel.Branches%2A> colección de la actividad parallel, arrastre algún otro diseñador de actividad de la **cuadro de herramientas** y colóquelo en el triángulo dentro de la **paralelo** Diseñador de actividad. Los triángulos rodean las actividades contenidas en las bifurcaciones. Las actividades adicionales se pueden agregar repitiendo este procedimiento. Las actividades se pueden reordenar arrastrándolas y colocándolas en el **paralelo** Diseñador de actividad.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Parallel en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las propiedades de la actividad Parallel y se describe cómo se usan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **paralelo**. El valor se puede editar en el **propiedades** cuadrícula o directamente en el encabezado del Diseñador de actividad.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la colección de actividades secundarias que se van a ejecutar.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Se evalúa cuando se completa una bifurcación. Si se evalúa como **True**, a continuación, el trabajo programado bifurcaciones pendientes se cancelan. Si esta propiedad no está establecida o se evalúa como **False**, la actividad se completa cuando se hayan completado todas sus actividades secundarias. El valor predeterminado es **null**.|

## <a name="see-also"></a>Vea también

- [secuencia](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)