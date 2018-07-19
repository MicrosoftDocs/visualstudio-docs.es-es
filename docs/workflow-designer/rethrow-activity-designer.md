---
title: Diseñador de flujo de trabajo - Diseñador de actividades Rethrow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c13b629047b73b3f3ee15f2fc25a0120a2c177
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755260"
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
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)