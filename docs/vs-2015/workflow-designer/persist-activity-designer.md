---
title: Diseñador de actividad Persist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60a63dd4036863641646e85a89f5018cba786802
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672621"
---
# <a name="persist-activity-designer"></a>Diseñador de actividades Persist
El diseñador de actividades **Persist** se usa para crear y configurar una <xref:System.Activities.Statements.Persist> actividad.

## <a name="the-persist-activity"></a>Actividad Persist
 La actividad <xref:System.Activities.Statements.Persist> guarda un flujo de trabajo en el disco, si es posible. La actividad <xref:System.Activities.Statements.Persist> no se puede ejecutar en una zona que no sea de persistencia como, por ejemplo, dentro de una actividad <xref:System.Activities.Statements.TransactionScope>. Si utiliza una actividad <xref:System.Activities.Statements.Persist> en un ámbito que no sea de persistencia, se produce una excepción en tiempo de ejecución.

### <a name="using-the-persist-activity-designer"></a>Utilizar el diseñador de actividades Persist
 El diseñador de actividades **Persist** se puede encontrar en la categoría **tiempo de ejecución** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **Persist** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.Persist> actividad con un valor **displayName** predeterminado de Persist. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **Persist** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-persist-properties"></a>Propiedades Persist
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Persist> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Persist>. El valor predeterminado es Persist. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|

## <a name="see-also"></a>Consulte también
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [en tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)