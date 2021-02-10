---
title: 'Diseñador de flujo de trabajo: iniciar el diseñador de actividades'
description: Obtenga información sobre la actividad Throw y cómo puede utilizar el diseñador de actividades Throw para crear y configurar una actividad Throw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1ffd0a9dda243e53431e419910b866853cd3932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969104"
---
# <a name="throw-activity-designer"></a>Diseñador de actividades Throw

El diseñador de actividades **Throw** se utiliza para crear y configurar una <xref:System.Activities.Statements.Throw> actividad.

## <a name="the-throw-activity"></a>Actividad Throw

La actividad <xref:System.Activities.Statements.Throw> produce una excepción.

### <a name="using-the-throw-activity-designer"></a>Utilizar el diseñador de actividades Throw

Obtenga acceso al diseñador de actividades **Throw** en la categoría **control de errores** del **cuadro de herramientas**.

El diseñador de actividades **Throw** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.Throw> actividad con un valor **displayName** predeterminado de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **Throw** o en el cuadro **displayName** de la cuadrícula de propiedades. La propiedad <xref:System.Activities.Statements.Throw.Exception%2A> se debe editar en la cuadrícula de propiedades.

### <a name="the-throw-properties"></a>Propiedades Throw

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Throw> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Throw>. El valor predeterminado es Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Excepción que se va a producir. Esta excepción debe derivar de <xref:System.Exception>. Para especificar la excepción, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Diseñador de actividad Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
