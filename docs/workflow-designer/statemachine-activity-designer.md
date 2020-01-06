---
title: Diseñador de actividades Diseñador de flujo de trabajo-StateMachine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: e7a270780a953a6104adc7089a02ff6529106fdf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593140"
---
# <a name="statemachine-activity-designer"></a>Diseñador de actividades StateMachine

La actividad <xref:System.Activities.Statements.StateMachine> contiene una colección de flujos de trabajo de estados y modelos que usan el paradigma conocido de máquina de estados.

## <a name="using-the-statemachine-activity-designer"></a>Usar el diseñador de actividad StateMachine

Para agregar una actividad <xref:System.Activities.Statements.StateMachine>, arrastre el diseñador de actividad **StateMachine** desde la sección **máquina de Estados** del **cuadro de herramientas** y colóquelo en la superficie de diseñador de flujo de trabajo. Para agregar un estado secundario a esta actividad <xref:System.Activities.Statements.StateMachine>, arrastre un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> desde el **cuadro de herramientas** y colóquelo en **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad StateMachine en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.StateMachine> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador .

|Nombre de la propiedad|Requerido|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.StateMachine> en el encabezado. El valor predeterminado es **StateMachine**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Activity.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
