---
title: Diseñador de actividad en paralelo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f557eb013cb313321b336fb22fd1299e51faaa82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221593"
---
# <a name="parallel-activity-designer"></a>Diseñador de actividades Parallel
La actividad de la clase <xref:System.Activities.Statements.Parallel> ejecuta una colección de actividades secundarias simultáneamente.  
  
## <a name="the-parallel-activity"></a>La actividad de la clase Parallel  
 La actividad de la clase <xref:System.Activities.Statements.Parallel> almacena sus actividades secundarias en una colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A>. Use la actividad de la clase <xref:System.Activities.Statements.Parallel> en vez de la actividad de la clase <xref:System.Activities.Statements.Sequence> si alguna de las actividades secundarias se puede quedar inactiva.  
  
 La actividad <xref:System.Activities.Statements.Parallel> tiene una propiedad <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contiene a una expresión [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] especificada por el usuario. La actividad <xref:System.Activities.Statements.Parallel> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad se completa sin ejecutar las demás ramas. Si el <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> no se evalúa como **True**, la <xref:System.Activities.Statements.Parallel> actividad se completa cuando se hayan completado todas sus actividades secundarias.  
  
### <a name="using-the-parallel-activity-designer"></a>Usar el diseñador de actividad Parallel  
 El **paralelo** Diseñador de actividad puede encontrarse en el **flujo de Control** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **paralelo** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde los diseñadores de actividad se coloquen normalmente, por ejemplo, dentro de un **Secuencia** Diseñador de actividad. Después de colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)], crea un <xref:System.Activities.Statements.Parallel> actividad, que de forma predeterminada, contiene un <xref:System.Activities.Activity.DisplayName%2A> de **paralelo**  
  
 Para agregar una actividad para el <xref:System.Activities.Statements.Parallel.Branches%2A> colección de la actividad parallel, arrastre algún otro diseñador de actividad desde el **cuadro de herramientas** y colóquelo en el triángulo dentro de la **paralelo** Diseñador de actividad. Los triángulos rodean las actividades contenidas en las bifurcaciones. Las actividades adicionales se pueden agregar repitiendo este procedimiento. Las actividades se pueden reordenar arrastrándolos y colocándolos en la **paralelo** Diseñador de actividad.  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Parallel en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de la actividad Parallel y se describe cómo se usan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **paralelo**. El valor se puede editar, opcionalmente, en el **propiedades** cuadrícula o directamente en el encabezado del Diseñador de actividad.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la colección de actividades secundarias que se van a ejecutar.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Se evalúa cuando se completa una bifurcación. Si se evalúa como **True**, a continuación, programados bifurcaciones pendientes se cancelan. Si esta propiedad no se ha establecido o se evalúa como **False**, la actividad se completa cuando se hayan completado todas sus actividades secundarias. El valor predeterminado es **null**.|  
  
## <a name="see-also"></a>Vea también  
 [Secuencia](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)