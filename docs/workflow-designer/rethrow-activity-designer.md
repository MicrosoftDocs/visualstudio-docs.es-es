---
title: Diseñador de flujo de trabajo - Diseñador de actividades Rethrow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 558ff5a36d172b8cd1fef0b811d1eaa920b90c6d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913881"
---
# <a name="rethrow-activity-designer"></a>Diseñador de actividades Rethrow

El **Rethrow** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Rethrow> actividad.

## <a name="the-rethrow-activity"></a>La actividad Rethrow

La actividad <xref:System.Activities.Statements.Rethrow> produce un excepción que ya se había producido anteriormente. Esta actividad solo se puede utilizar en un controlador <xref:System.Activities.Statements.Catch> en la actividad <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Utilice el Diseñador de actividades ReThrow

Acceso a la **Rethrow** Diseñador de actividad en el **control de errores** categoría de la **cuadro de herramientas**. El **Rethrow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.Rethrow> actividad con un valor predeterminado **DisplayName** de Throw. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **Rethrow** Diseñador de actividad, o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-rethrow-properties"></a>Propiedades Rethrow

La tabla siguiente muestra la <xref:System.Activities.Statements.Rethrow> propiedades y se describe cómo se usan en el diseñador:

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)