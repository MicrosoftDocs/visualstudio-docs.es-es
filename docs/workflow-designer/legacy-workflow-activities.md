---
title: Las actividades de flujo de trabajo heredado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: 8a5c35fb036c1d9a94bd42c5ceabe17ae65e7b7c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="legacy-workflow-activities"></a>Actividades de flujo de trabajo heredadas
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] contiene un conjunto predeterminado de actividades que proporcionan la funcionalidad para el flujo de control, las condiciones, el control de eventos, la administración de estados, así como la comunicación con aplicaciones y servicios. Al diseñar flujos de trabajo, puede usar las actividades proporcionadas por el sistema que proporciona [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] o crear sus propias actividades personalizadas.  
  
 En la tabla siguiente se mencionan las actividades predeterminadas de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Aunque no todas, muchas de estas actividades están representadas por los diseñadores de actividades que pueden tener acceso desde el **cuadro de herramientas** de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Para crear una actividad, arrastre el diseñador desde el **cuadro de herramientas** y colóquela en la superficie de diseño.  
  
|Actividad|Descripción|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Usar con el **HandleExternalEventActivity** actividad para las comunicaciones de entrada y salidas con un servicio local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Se utiliza para contener la lógica de limpieza para una actividad compuesta cancelada antes de que se terminen de ejecutar todos los elementos secundarios de la actividad compuesta. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Permite agregar código de Visual Basic o de C# al flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Una versión compensable de [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Una versión compensable de **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Permite llamar al código para deshacer o compensar las operaciones ya realizadas por el flujo de trabajo cuando se produce un error. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Un contenedor para una o varias actividades que realizan la compensación para una actividad TransactionScopeActivity completada [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [mediante la actividad CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Ejecuta actividades secundarias basadas en una condición que se aplica a la [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) propia actividad y según las condiciones que se aplican por separado a cada elemento secundario. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Le permite compilar retrasos en el flujo de trabajo, basados en un intervalo de tiempo de espera. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Ajusta una o varias actividades que se ejecutan cuando se produce un evento especificado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Proporciona un marco de trabajo para asociar eventos a una actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Ejecuta su actividad secundaria principal al mismo tiempo un [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Se usa para controlar una excepción del tipo especificado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Representa una actividad compuesta que tiene una lista ordenada de actividades secundarias de tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Usa junto con el [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) actividad para las comunicaciones de entrada y salidas con un servicio local. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Comprueba una condición en cada bifurcación y realiza actividades en la primera bifurcación para el que la condición es **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Representa una bifurcación de un [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Permite que el flujo de trabajo invoque un servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Permite que el flujo de trabajo invoque otro flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[Actividad ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Una actividad compuesta que contiene solo [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) actividades secundarias. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de la actividad ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Proporciona una manera de programar dos o más secundarios **SequenceActivity** ramas de actividad para el procesamiento al mismo tiempo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Se usa para representar una colección de reglas. Regla formada por condiciones y las acciones resultantes. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crea varias instancias de una única actividad secundaria. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Proporciona una manera sencilla de vincular varias actividades para su ejecución secuencial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa un estado en un flujo de trabajo de equipo de estado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Usar en un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) actividad como un contenedor de actividades secundarias ejecutadas al dejar la **StateActivity** actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Usar en un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) actividad como un contenedor de actividades secundarias ejecutadas al entrar los **StateActivity** actividad. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Suspende la operación del flujo de trabajo para permitir la intervención si se produce alguna condición de error que requiere atención especial. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Ejecuta secuencialmente las actividades contenidas en un dominio sincronizado. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Permite finalizar inmediatamente el funcionamiento del flujo de trabajo si se produce una condición de error. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Permite capturar excepciones de empresa iniciadas como parte de los metadatos de proceso para un flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Proporciona un marco de trabajo para controlar las transacciones y las excepciones. Para obtener más información, consulte [mediante la actividad TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Permite crear el modelo de la instancia de un error de servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Recibe los datos de un servicio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Responde a una solicitud de servicio Web realizada a un flujo de trabajo. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Permite que el flujo de trabajo se ejecute en bucle hasta que se cumpla una condición. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Uso de la actividad de WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
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