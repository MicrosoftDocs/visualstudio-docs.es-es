---
title: 'Diseñador de flujo de trabajo: volver a generar el diseñador de actividades'
description: Obtenga información sobre la actividad Rethrow y cómo usar el diseñador de actividades Rethrow para crear y configurar una actividad Rethrow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e3615c73583e8c5c313d23fd5f9aa6d9fcd5ff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847328"
---
# <a name="rethrow-activity-designer"></a>Diseñador de actividades Rethrow

El diseñador de actividades **Rethrow** se utiliza para crear y configurar una <xref:System.Activities.Statements.Rethrow> actividad.

## <a name="the-rethrow-activity"></a>La actividad Rethrow

La actividad <xref:System.Activities.Statements.Rethrow> produce un excepción que ya se había producido anteriormente. Esta actividad solo se puede utilizar en un controlador <xref:System.Activities.Statements.Catch> en la actividad <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Usar el diseñador de actividades Rethrow

Obtenga acceso al diseñador de actividades **Rethrow** en la categoría **control de errores** del **cuadro de herramientas**. El diseñador de actividades **Rethrow** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo dondequiera que se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.Rethrow> actividad con un valor **displayName** predeterminado de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **Rethrow** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-rethrow-properties"></a>Propiedades de Rethrow

En la tabla siguiente se muestran las <xref:System.Activities.Statements.Rethrow> propiedades y se describe cómo se usan en el diseñador:

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [NotImplementedException](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
