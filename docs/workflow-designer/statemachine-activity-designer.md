---
title: Diseñador de flujo de trabajo - Diseñador de actividades StateMachine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6a9860d4c6025e6d77a869573b133c6a034aff96
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974928"
---
# <a name="statemachine-activity-designer"></a>Diseñador de actividades StateMachine

La actividad <xref:System.Activities.Statements.StateMachine> contiene una colección de flujos de trabajo de estados y modelos que usan el paradigma conocido de máquina de estados.

## <a name="using-the-statemachine-activity-designer"></a>Usar el diseñador de actividad StateMachine

Para agregar un <xref:System.Activities.Statements.StateMachine> actividad, arrastre el **StateMachine** Diseñador de actividad desde la **máquina de estados** sección de la **cuadro de herramientas** y colóquela en el flujo de trabajo de Windows Superficie del diseñador. Para agregar un estado secundario a esta <xref:System.Activities.Statements.StateMachine> actividad, arrastre un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> desde el **cuadro de herramientas** y colóquela sobre la **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad StateMachine en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.StateMachine> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador .

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.StateMachine> en el encabezado. El valor predeterminado es **StateMachine**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Activity.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)