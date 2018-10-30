---
title: Diseñador de flujo de trabajo - Diseñador de actividad StateMachine
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
ms.openlocfilehash: 379364ad443c947ea0cd44e2ed58d2b0ca988f72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880537"
---
# <a name="statemachine-activity-designer"></a>Diseñador de actividades StateMachine

La actividad <xref:System.Activities.Statements.StateMachine> contiene una colección de flujos de trabajo de estados y modelos que usan el paradigma conocido de máquina de estados.

## <a name="using-the-statemachine-activity-designer"></a>Usar el diseñador de actividad StateMachine

Para agregar un <xref:System.Activities.Statements.StateMachine> actividad, arrastre el **StateMachine** Diseñador de actividades desde el **máquina de estados** sección de la **cuadro de herramientas** y colóquelo en el Diseñador de flujo de trabajo superficie. Para agregar un estado secundario a esta <xref:System.Activities.Statements.StateMachine> actividad, arrastre un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> desde el **cuadro de herramientas** y colóquela en la **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad StateMachine en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.StateMachine> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador .

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.StateMachine> en el encabezado. El valor predeterminado es **StateMachine**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Activity.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)