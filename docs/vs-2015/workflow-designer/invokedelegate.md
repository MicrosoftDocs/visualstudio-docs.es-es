---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659004"
---
# <a name="invokedelegate"></a>InvokeDelegate

El diseñador de **InvokeDelegate** se usa para crear y configurar una <xref:System.Activities.Statements.InvokeDelegate> actividad.

## <a name="the-invokedelegate-activity"></a>Actividad InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> llama a un delegado público.

### <a name="using-the-invokedelegate-activity-designer"></a>Usar el diseñador de actividad InvokeDelegate

El diseñador de actividades **InvokeDelegate** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

El diseñador de actividades **InvokeDelegate** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se colocan normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . De esta forma, se crea una actividad <xref:System.Activities.Statements.InvokeDelegate> con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **InvokeDelegate** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-invokedelegate-properties"></a>Las propiedades de InvokeDelegate

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.InvokeDelegate> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.InvokeDelegate>. El valor predeterminado es InvokeDelegate.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Verdadero|El nombre del <xref:System.Activities.ActivityDelegate> que se va a llamar cuando se ejecute la actividad. Esta propiedad se puede editar en la superficie del diseñador. Es una propiedad obligatoria.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falso|La colección de argumentos del delegado llamado. Las claves son los nombres de los objetos <xref:System.Activities.DelegateArgument> incluidos en el <xref:System.Activities.ActivityDelegate> y los valores son los argumentos cuyas expresiones se evalúan y asignan a los objetos <xref:System.Activities.DelegateArgument> correspondientes. En la cuadrícula de propiedades, haga clic en el botón de puntos suspensivos en el campo **DelegateArguments** , que muestra el cuadro de diálogo **DelegateArguments** para permitirle establecer esta propiedad. Haga clic en el campo **crear argumento** para agregar los argumentos.|

## <a name="see-also"></a>Consulte también

- [Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)