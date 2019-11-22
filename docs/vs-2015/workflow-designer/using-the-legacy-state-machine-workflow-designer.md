---
title: Using the Legacy State Machine Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302808"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Usar el diseñador de flujo de trabajo de máquina de estados heredado
When you are creating a new state machine workflow project in [!INCLUDE[vs2010](../includes/vs2010-md.md)] that targets either the [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] or the [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], you can choose to use either the **State Machine Workflow Console Application** or the **State Machine Workflow Library** legacy project template. Si elige una de estas plantillas de proyecto de máquina de estados, el diseñador de máquina de estados se presenta como la interfaz de usuario del diseñador de flujo de trabajo heredada. For information about the legacy state machine project templates, see [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) and [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Un flujo de trabajo de equipo de estado está compuesto por un conjunto de estados. Se designa un estado como estado inicial. Cada estado puede recibir un conjunto de eventos determinado. En función de un evento, se puede realizar una transición a otro estado. El flujo de trabajo de equipo de estado puede tener un estado final. Cuando se realiza una transición al estado final, el flujo de trabajo termina.

## <a name="state-machine-designer-views"></a>Vistas del diseñador de equipo de estado
 El diseñador de equipo de estado es un diseñador de forma libre, lo que significa que las actividades se pueden mover libremente por la superficie de diseño. The state machine designer has two views: *state* view and *event-driven* view.

 La vista de estado muestra las actividades de estado y las actividades orientadas a eventos que pueden estar dentro de una actividad de estado. En esta vista, las transiciones de un estado a otro se representan mediante líneas que van de la actividad orientada a eventos en un estado a otro estado. También puede crear las transiciones dibujando la línea usted mismo. Para dibujar la transición, seleccione la actividad orientada a eventos y, a continuación, seleccione uno de los controladores de la actividad y arrástrelo. Esta acción dibuja una línea. A continuación, la línea se adjunta al estado de destino, lo que indica una transición entre estados.

 Para tener acceso a la vista orientada a eventos, haga doble clic en una actividad orientada a eventos. El diseñador que aparece es muy parecido al diseñador de flujo de trabajo secuencial. En la parte superior del diseñador, una barra de exploración muestra la jerarquía de las actividades hasta la actividad orientada a eventos que se aparece. Puede volver a la vista de estado haciendo clic en cualquier elemento de la jerarquía que se muestra. Si ha dibujado una transición de un estado a otro en la vista de estado, y si está en la vista orientada a eventos de esa actividad, se agrega una actividad de estado fija a la actividad orientada a eventos. Si cambia las propiedades de la actividad de estado fija, el cambio queda reflejado en la vista de estado.

## <a name="state-machine-workflow-activities"></a>Actividades de flujo de trabajo de equipo de estado
 En la tabla siguiente se describen las actividades principales que se utilizan en un diseñador de flujo de trabajo de máquina de estados.

|Nombre del cuadro de herramientas|Actividad|Descripción|
|------------------|--------------|-----------------|
|**Estado**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Represents a state in a state machine; may contain additional **StateActivity** activities. For more information, see [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado. For more information, see [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Se ejecuta cuando se entra en un estado; puede contener otras actividades. For more information, see [Using the StateInitialization Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Executes contained activities when leaving a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. For more information, see [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Se utiliza para los estados que dependen de un evento externo para empezar a ejecutarse. The **EventDrivenActivity** activity must have an activity that implements the [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) interface as the first child activity. For more information, see [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|

 The main component in a state machine workflow is the [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. Al capturarse eventos en diversos puntos en un flujo de trabajo de equipo de estado, se entra en estados diferentes para administrar las tareas asociadas a los eventos. Durante la duración del flujo de trabajo, éste puede entrar en y salir de varios estados diferentes. These states connect to each other by using the [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) activity.

 When you drag a new **StateActivity** onto the workflow design surface, you can add [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043), or additional **StateActivity** activities as child activities.

> [!CAUTION]
> When you use the state machine workflow designer to create workflows, you must monitor the structure of the workflow you are designing with the **Document Outline** view window. The view of the structure of the state machine workflow in the **Document Outline** view window mirrors the logical layout of the activities in the workflow markup file. El diseño físico de las actividades de flujo de trabajo tal como aparecen en la superficie de diseño podría no reflejar el diseño lógico de las actividades del archivo de marcado del flujo de trabajo.
>
> To open the **Document Outline** window, on the **View** menu, point to **Other Windows**, and then select **Document Outline**.

## <a name="see-also"></a>Vea también
 [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [State Machine Workflows](https://go.microsoft.com/fwlink?LinkID=65016) [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083) [Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006) [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008) [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082) [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068)