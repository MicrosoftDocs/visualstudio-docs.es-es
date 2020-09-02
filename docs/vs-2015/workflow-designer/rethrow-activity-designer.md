---
title: Rethrow (diseñador de actividades) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663365"
---
# <a name="rethrow-activity-designer"></a>Diseñador de actividades Rethrow
El diseñador de actividades **Rethrow** se utiliza para crear y configurar una <xref:System.Activities.Statements.Rethrow> actividad.

## <a name="the-rethrow-activity"></a>Actividad Rethrow
 La actividad <xref:System.Activities.Statements.Rethrow> produce un excepción que ya se había producido anteriormente. Esta actividad solo se puede utilizar en un controlador <xref:System.Activities.Statements.Catch> en la actividad <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilizar el diseñador de actividades ReThrow
 El diseñador de actividades **Rethrow** se puede encontrar en la categoría **control de errores** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **Rethrow** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.Rethrow> actividad con un valor **displayName** predeterminado de Throw. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **Rethrow** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-rethrow-properties"></a>Propiedades Rethrow
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Rethrow> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Rethrow>. El valor predeterminado es Rethrow.|

## <a name="see-also"></a>Consulte también
 [Collection](../workflow-designer/collection-activity-designers.md) [Generar](../workflow-designer/throw-activity-designer.md) la colección [TryCatch](../workflow-designer/trycatch-activity-designer.md)