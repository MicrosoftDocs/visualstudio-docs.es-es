---
title: Los diseñadores de actividades de flujo de control | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e852bfa5b392c6ffa758678fa83dabd8a8c97f54
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303620"
---
# <a name="control-flow-activity-designers"></a>Diseñadores de actividades de flujos de control
[!INCLUDE[wfd1](../includes/wfd1-md.md)] incluye varias actividades proporcionadas por el sistema que puede utilizar cuando cree flujos de trabajo. En esta sección se incluyen las actividades proporcionadas por el sistema que se utilizan para controlar el flujo dentro de un flujo de trabajo. Los siguientes temas describen estas actividades y ofrecen orientación sobre cómo utilizarlas.  
  
## <a name="in-this-section"></a>En esta sección  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 Ejecuta la actividad contenida en el cuerpo de al menos una vez, hasta que una condición especificada se evalúa como **true**.  
  
 [ForEach\<T >](http://msdn.microsoft.com/en-us/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 Ejecuta la actividad que se incluye en el cuerpo para cada elemento en una colección especificada.  
  
 [If](../workflow-designer/if-activity-designer.md)  
 Evalúa una condición y ejecuta una actividad según los resultados de esa evaluación.  
  
 [Parallel](../workflow-designer/parallel-activity-designer.md)  
 Ejecuta una colección de actividades secundarias simultáneamente.  
  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)  
 Enumera los elementos de una colección y ejecuta una instrucción incrustada para cada elemento de la colección en paralelo.  
  
 [Pick](../workflow-designer/pick-activity-designer.md)  
 Ejecuta una de las diversas bifurcaciones como respuesta a algún evento que proporciona un control de flujo basado en eventos.  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 Proporciona una ruta de acceso de ejecución potencial dentro de una actividad <xref:System.Activities.Statements.Pick>.  
  
 [Sequence](../workflow-designer/sequence-activity-designer.md)  
 Contiene una colección ordenada de actividades secundarias que ejecuta por orden.  
  
 [Conmutador\<T >](http://msdn.microsoft.com/en-us/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 Evalúa una expresión especificada y ejecuta la actividad desde una colección de actividades cuya clave asociada se corresponde con el valor que se ha obtenido a partir de la evaluación.  
  
 [While](../workflow-designer/while-activity-designer.md)  
 Ejecuta la actividad contenida en su cuerpo mientras una condición especificada se evalúa como **true**.  
  
## <a name="reference"></a>Referencia  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## <a name="related-sections"></a>Secciones relacionadas  
 Para otros tipos de diseñadores de actividades, vea los siguientes temas.  
  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)  
  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)  
  
 [Messaging](../workflow-designer/messaging-activity-designers.md)  
  
 [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)  
  
 [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)  
  
 [Transacción](../workflow-designer/transaction-activity-designers.md)  
  
 [Colección](../workflow-designer/collection-activity-designers.md)  
  
 [Control de errores](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>Recursos externos  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)