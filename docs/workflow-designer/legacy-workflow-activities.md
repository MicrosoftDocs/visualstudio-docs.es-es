---
title: Las actividades de flujo de trabajo heredado | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ae0cef2943abffe947c179f9cfcd6c2223931337
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="legacy-workflow-activities"></a>Actividades de flujo de trabajo heredadas
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] contiene un conjunto predeterminado de actividades que proporcionan la funcionalidad para el flujo de control, las condiciones, el control de eventos, la administración de estados, así como la comunicación con aplicaciones y servicios. Al diseñar flujos de trabajo, puede usar las actividades proporcionadas por el sistema que proporciona [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] o crear sus propias actividades personalizadas.  
  
 En la tabla siguiente se mencionan las actividades predeterminadas de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Aunque no todas, muchas de estas actividades están representadas por los diseñadores de actividades que pueden tener acceso desde el **cuadro de herramientas** de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Para crear una actividad, arrastre el diseñador desde el **cuadro de herramientas** y colóquela en la superficie de diseño.  
  
|Actividad|Descripción|  
|--------------|-----------------|  
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Usar con el **HandleExternalEventActivity** actividad para las comunicaciones de entrada y salidas con un servicio local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|**System.Workflow.Activities.CancellationHandlerActivity**|Se utiliza para contener la lógica de limpieza para una actividad compuesta cancelada antes de que se terminen de ejecutar todos los elementos secundarios de la actividad compuesta. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|<xref:System.Workflow.Activities.CodeActivity>|Permite agregar código de Visual Basic o de C# al flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Versión compensable de <xref:System.Workflow.Activities.SequenceActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Una versión compensable de **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|**System.Workflow.Activities.CompensateActivity**|Permite llamar al código para deshacer o compensar las operaciones ya realizadas por el flujo de trabajo cuando se produce un error. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|**System.Workflow.Activities.CompensationHandlerActivity**|Un contenedor para una o varias actividades que realizan la compensación para una actividad TransactionScopeActivity completada [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [mediante la actividad CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Ejecuta actividades secundarias basadas en una condición que se aplica a la propia actividad <xref:System.Workflow.Activities.ConditionedActivityGroup>, y en condiciones que se aplican independientemente a cada elemento secundario. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|<xref:System.Workflow.Activities.DelayActivity>|Le permite compilar retrasos en el flujo de trabajo, basados en un intervalo de tiempo de espera. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|<xref:System.Workflow.Activities.EventDrivenActivity>|Ajusta una o varias actividades que se ejecutan cuando se produce un evento especificado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|<xref:System.Workflow.Activities.EventHandlersActivity>|Proporciona un marco de trabajo para asociar eventos a una actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Ejecuta su actividad secundaria principal al mismo tiempo un <xref:System.Workflow.Activities.EventHandlersActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|**System.Workflow.Activities.FaultHandlerActivity**|Se usa para controlar una excepción del tipo especificado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|**System.Workflow.Activities.FaultHandlersActivity**|Representa una actividad compuesta que tiene una lista ordenada de actividades secundarias de tipo **System.Workflow.Activities.FaultHandlerActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Usa junto con la <xref:System.Workflow.Activities.CallExternalMethodActivity> actividad para las comunicaciones de entrada y salidas con un servicio local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|<xref:System.Workflow.Activities.IfElseActivity>|Comprueba una condición en cada bifurcación y realiza actividades en la primera bifurcación para el que la condición es **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Representa una bifurcación de un <xref:System.Workflow.Activities.IfElseActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Permite que el flujo de trabajo invoque un servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Permite que el flujo de trabajo invoque otro flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|<xref:System.Workflow.Activities.ListenActivity>|Actividad compuesta que contiene sólo actividades secundarias <xref:System.Workflow.Activities.EventDrivenActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de la actividad ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|<xref:System.Workflow.Activities.ParallelActivity>|Proporciona una manera de programar dos o más secundarios **SequenceActivity** ramas de actividad para el procesamiento al mismo tiempo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|<xref:System.Workflow.Activities.PolicyActivity>|Se usa para representar una colección de reglas. Regla formada por condiciones y las acciones resultantes. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|<xref:System.Workflow.Activities.ReplicatorActivity>|Crea varias instancias de una única actividad secundaria. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|<xref:System.Workflow.Activities.SequenceActivity>|Proporciona una manera sencilla de vincular varias actividades para su ejecución secuencial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|<xref:System.Workflow.Activities.SetStateActivity>|Especifica una transición a un nuevo estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|<xref:System.Workflow.Activities.StateActivity>|Representa un estado en un flujo de trabajo de equipo de estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Usar en un <xref:System.Workflow.Activities.StateActivity> actividad como un contenedor de actividades secundarias ejecutadas al dejar la **StateActivity** actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|<xref:System.Workflow.Activities.StateInitializationActivity>|Usar en un <xref:System.Workflow.Activities.StateActivity> actividad como un contenedor de actividades secundarias ejecutadas al entrar los **StateActivity** actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**System.Workflow.Activities.SuspendActivity**|Suspende la operación del flujo de trabajo para permitir la intervención si se produce alguna condición de error que requiere atención especial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|**System.Workflow.Activities.SynchronizationScopeActivity**|Ejecuta secuencialmente las actividades contenidas en un dominio sincronizado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|**System.Workflow.Activities.TerminateActivity**|Permite finalizar inmediatamente el funcionamiento del flujo de trabajo si se produce una condición de error. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|**System.Workflow.Activities.ThrowActivity**|Permite capturar excepciones de empresa iniciadas como parte de los metadatos de proceso para un flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|**System.Workflow.Activities.TransactionScopeActivity**|Proporciona un marco de trabajo para controlar las transacciones y las excepciones. Para obtener más información, consulte [mediante la actividad TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Permite crear el modelo de la instancia de un error de servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Recibe los datos de un servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Responde a una solicitud de servicio Web realizada a un flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|<xref:System.Workflow.Activities.WhileActivity>|Permite que el flujo de trabajo se ejecute en bucle hasta que se cumpla una condición. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]cómo crear actividades personalizadas, consulte [desarrollar actividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65023) y [mediante el Diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md)  
 Describe las vistas de diseño diferentes de actividades.  
  
 [Cómo: Agregar actividades al cuadro de herramientas (heredado)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Muestra cómo agregar actividades al cuadro de herramientas.  
  
 [Cómo: Crear una condición de regla declarativa (heredado)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Muestra los pasos para crear una condición de regla declarativa.  
  
 [Cómo: Crear un conjunto de reglas para PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Muestra los pasos para crear un conjunto de reglas de PolicyActivity.  
  
 [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Muestra los pasos para implementar una operación de contrato [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
 [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Muestra los pasos para invocar una operación de contrato [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Actividades de Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Desarrollo de flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Desarrollar actividades de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65023)