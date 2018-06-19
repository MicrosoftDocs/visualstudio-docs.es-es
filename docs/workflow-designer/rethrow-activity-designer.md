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
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973841"
---
# <a name="rethrow-activity-designer"></a>Diseñador de actividades Rethrow

El **a producir** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Rethrow> actividad.

## <a name="the-rethrow-activity"></a>Actividad Rethrow
 La actividad <xref:System.Activities.Statements.Rethrow> produce un excepción que ya se había producido anteriormente. Esta actividad solo se puede utilizar en un controlador <xref:System.Activities.Statements.Catch> en la actividad <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilizar el diseñador de actividades ReThrow
 El **a producir** Diseñador de actividad puede encontrarse en el **control de errores** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha en el lado izquierdo del Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **a producir** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.Rethrow> actividad con el valor predeterminado es **DisplayName** de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **a producir** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-rethrow-properties"></a>Propiedades Rethrow
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Rethrow> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)