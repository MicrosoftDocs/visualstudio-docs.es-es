---
title: Las actividades de flujo de trabajo heredado | Documentos de Microsoft
ms.date: 01/18/2017
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f31ff7ac208d4b06ce454ef309d35400cb79f97
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-workflow-activities"></a>Actividades de flujo de trabajo heredadas

[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] contiene un conjunto predeterminado de actividades que proporcionan la funcionalidad para el flujo de control, las condiciones, el control de eventos, la administración de estados, así como la comunicación con aplicaciones y servicios. Al diseñar flujos de trabajo, puede usar las actividades proporcionadas por el sistema que se proporcionan con el Diseñador de flujo de trabajo de Windows, o puede crear sus propias actividades personalizadas.

 En la tabla siguiente se mencionan las actividades predeterminadas de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Aunque no todas, muchas de estas actividades están representadas por los diseñadores de actividades que pueden tener acceso desde el **cuadro de herramientas** de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Para crear una actividad, arrastre el diseñador desde el **cuadro de herramientas** y colóquela en la superficie de diseño.

|Actividad|Descripción|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Usar con el **HandleExternalEventActivity** actividad para las comunicaciones de entrada y salidas con un servicio local. Para obtener más información, consulte [mediante la actividad CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Se utiliza para contener la lógica de limpieza para una actividad compuesta cancelada antes de que se terminen de ejecutar todos los elementos secundarios de la actividad compuesta. Para obtener más información, consulte [mediante la actividad CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Permite agregar código de Visual Basic o de C# al flujo de trabajo. Para obtener más información, consulte [mediante la actividad de CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Versión compensable de <xref:System.Workflow.Activities.SequenceActivity>. Para obtener más información, consulte [mediante la actividad CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Una versión compensable de **TransactionScopeActivity**. Para obtener más información, consulte [mediante la actividad CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Permite llamar al código para deshacer o compensar las operaciones ya realizadas por el flujo de trabajo cuando se produce un error. Para obtener más información, consulte [mediante la actividad CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Un contenedor para una o varias actividades que realizan la compensación para una actividad TransactionScopeActivity completada para obtener más información, vea [mediante la actividad CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Ejecuta actividades secundarias basadas en una condición que se aplica a la propia actividad <xref:System.Workflow.Activities.ConditionedActivityGroup>, y en condiciones que se aplican independientemente a cada elemento secundario. Para obtener más información, consulte [mediante la actividad ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Le permite compilar retrasos en el flujo de trabajo, basados en un intervalo de tiempo de espera. Para obtener más información, consulte [mediante la actividad DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Ajusta una o varias actividades que se ejecutan cuando se produce un evento especificado. Para obtener más información, consulte [mediante la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Proporciona un marco de trabajo para asociar eventos a una actividad. Para obtener más información, consulte [mediante la actividad EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Ejecuta su actividad secundaria principal al mismo tiempo un <xref:System.Workflow.Activities.EventHandlersActivity>. Para obtener más información, consulte [mediante la actividad EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Se usa para controlar una excepción del tipo especificado. Para obtener más información, consulte [mediante la actividad FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Representa una actividad compuesta que tiene una lista ordenada de actividades secundarias de tipo **System.Workflow.Activities.FaultHandlerActivity**. Para obtener más información, consulte [mediante la actividad FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Usa junto con la <xref:System.Workflow.Activities.CallExternalMethodActivity> actividad para las comunicaciones de entrada y salidas con un servicio local. Para obtener más información, consulte [mediante la actividad HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Comprueba una condición en cada bifurcación y realiza actividades en la primera bifurcación para el que la condición es **true**. Para obtener más información, consulte [mediante la actividad IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Representa una bifurcación de un <xref:System.Workflow.Activities.IfElseActivity>. Para obtener más información, consulte [mediante la actividad IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Permite que el flujo de trabajo invoque un servicio Web. Para obtener más información, consulte [mediante la actividad InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Permite que el flujo de trabajo invoque otro flujo de trabajo. Para obtener más información, consulte [mediante la actividad InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Actividad compuesta que contiene sólo actividades secundarias <xref:System.Workflow.Activities.EventDrivenActivity>. Para obtener más información, consulte [mediante la actividad de la actividad ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Proporciona una manera de programar dos o más secundarios **SequenceActivity** ramas de actividad para el procesamiento al mismo tiempo. Para obtener más información, consulte [mediante la actividad ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|Se usa para representar una colección de reglas. Regla formada por condiciones y las acciones resultantes. Para obtener más información, consulte [mediante la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Crea varias instancias de una única actividad secundaria. Para obtener más información, consulte [mediante la actividad ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Proporciona una manera sencilla de vincular varias actividades para su ejecución secuencial. Para obtener más información, consulte [mediante la actividad SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Especifica una transición a un nuevo estado. Para obtener más información, consulte [mediante la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Representa un estado en un flujo de trabajo de equipo de estado. Para obtener más información, consulte [mediante la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Usar en un <xref:System.Workflow.Activities.StateActivity> actividad como un contenedor de actividades secundarias ejecutadas al dejar la **StateActivity** actividad. Para obtener más información, consulte [mediante la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Usar en un <xref:System.Workflow.Activities.StateActivity> actividad como un contenedor de actividades secundarias ejecutadas al entrar los **StateActivity** actividad. Para obtener más información, consulte [mediante la actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Suspende la operación del flujo de trabajo para permitir la intervención si se produce alguna condición de error que requiere atención especial. Para obtener más información, consulte [mediante la actividad SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Ejecuta secuencialmente las actividades contenidas en un dominio sincronizado. Para obtener más información, consulte [mediante la actividad SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Permite finalizar inmediatamente el funcionamiento del flujo de trabajo si se produce una condición de error. Para obtener más información, consulte [mediante la actividad TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Permite capturar excepciones de empresa iniciadas como parte de los metadatos de proceso para un flujo de trabajo. Para obtener más información, consulte [mediante la actividad ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Proporciona un marco de trabajo para controlar las transacciones y las excepciones. Para obtener más información, consulte [mediante la actividad TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Permite crear el modelo de la instancia de un error de servicio Web. Para obtener más información, consulte [mediante la actividad WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Recibe los datos de un servicio Web. Para obtener más información, consulte [mediante la actividad WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Responde a una solicitud de servicio Web realizada a un flujo de trabajo. Para obtener más información, consulte [mediante la actividad WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Permite que el flujo de trabajo se ejecute en bucle hasta que se cumpla una condición. Para obtener más información, consulte [mediante la actividad WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

 Para obtener más información acerca de cómo crear actividades personalizadas, consulte [desarrollar actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65023) y [mediante el Diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>Vea también

- [Actividades de Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)
- [Desarrollo de flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65010)
- [Desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65023)