---
title: Diseñador de flujo de trabajo InvokeDelegate
description: Obtenga información sobre el diseñador de InvokeDelegate y cómo puede usar el diseñador de InvokeDelegate para crear y configurar una actividad de InvokeDelegate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: a482f23b1df1587e9a1c7e3023bfb0d1737f1fae
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437754"
---
# <a name="invokedelegate"></a>InvokeDelegate

El diseñador de **InvokeDelegate** se usa para crear y configurar una <xref:System.Activities.Statements.InvokeDelegate> actividad.

## <a name="the-invokedelegate-activity"></a>La actividad InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> llama a un delegado público.

### <a name="use-the-invokedelegate-activity-designer"></a>Usar el diseñador de actividades InvokeDelegate

Acceda al diseñador de actividades **InvokeDelegate** en la categoría **primitivas** del **cuadro de herramientas**. El diseñador de actividades **InvokeDelegate** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo donde se colocan normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.InvokeDelegate> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **InvokeDelegate** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-invokedelegate-properties"></a>Propiedades de InvokeDelegate

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeDelegate> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeDelegate>. El valor predeterminado es InvokeDelegate.<br /><br /> Aunque <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesario, es mejor usar uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|El nombre del <xref:System.Activities.ActivityDelegate> que se va a llamar cuando se ejecute la actividad. Esta propiedad se puede editar en la superficie del diseñador y es obligatoria.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falso|La colección de argumentos del delegado llamado. Las claves son los nombres de los objetos de parámetro en y <xref:System.Activities.ActivityDelegate> los valores son los argumentos cuyas expresiones se evalúan y asignan a los objetos de parámetro correspondientes. Para mostrar el cuadro de diálogo **DelegateArguments** donde puede establecer esta propiedad, haga clic en el botón de puntos suspensivos en el campo **DelegateArguments** de la cuadrícula de propiedades. Haga clic en el campo **crear argumento** para agregar los argumentos.|

## <a name="see-also"></a>Consulte también

- [Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)