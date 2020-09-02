---
title: Iniciar el diseñador de actividad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1855daa5016241fb6eb04f05d7218e02083fc0a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655166"
---
# <a name="throw-activity-designer"></a>Diseñador de actividades Throw
El diseñador de actividades **Throw** se utiliza para crear y configurar una <xref:System.Activities.Statements.Throw> actividad.

## <a name="the-throw-activity"></a>Actividad Throw
 La actividad <xref:System.Activities.Statements.Throw> produce una excepción.

### <a name="using-the-throw-activity-designer"></a>Utilizar el diseñador de actividades Throw
 El diseñador de actividades **Throw** se puede encontrar en la categoría **control de errores** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **Throw** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.Throw> actividad con un valor **displayName** predeterminado de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **Throw** o en el cuadro **displayName** de la cuadrícula de propiedades. La propiedad <xref:System.Activities.Statements.Throw.Exception%2A> se debe editar en la cuadrícula de propiedades.

### <a name="the-throw-properties"></a>Propiedades Throw
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Throw> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Throw>. El valor predeterminado es Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Verdadero|Excepción que se va a producir. Esta excepción debe derivar de <xref:System.Exception>. Para especificar la excepción, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también
 [Colección](../workflow-designer/collection-activity-designers.md) de [reinicio](../workflow-designer/rethrow-activity-designer.md) de [actividad iniciar el diseñador de actividades](../workflow-designer/throw-activity-designer.md) [TryCatch](../workflow-designer/trycatch-activity-designer.md)