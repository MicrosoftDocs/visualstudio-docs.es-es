---
title: Actividades de flujo de trabajo heredadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302959"
---
# <a name="legacy-workflow-activities"></a>Actividades de flujo de trabajo heredadas
[!INCLUDE[wf](../includes/wf-md.md)] incluye un conjunto predeterminado de actividades que proporcionan funcionalidad para el flujo de control, las condiciones, el control de eventos, la administración de Estados y la comunicación con aplicaciones y servicios. Al diseñar flujos de trabajo, puede usar las actividades proporcionadas por el sistema que proporciona [!INCLUDE[wfd1](../includes/wfd1-md.md)] o crear sus propias actividades personalizadas.

 En la tabla siguiente se mencionan las actividades predeterminadas de [!INCLUDE[wf2](../includes/wf2-md.md)]. Muchas de estas actividades, pero no todas, se representan mediante diseñadores de actividad a los que se puede tener acceso desde el **cuadro de herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Para crear una actividad, arrastre su diseñador desde el **cuadro de herramientas** y colóquelo en la superficie de diseño.

|Actividad|Descripción|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Se utiliza con la actividad **HandleExternalEventActivity** para las comunicaciones de entrada y salida con un servicio local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Se utiliza para contener la lógica de limpieza para una actividad compuesta cancelada antes de que se terminen de ejecutar todos los elementos secundarios de la actividad compuesta. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Permite agregar código de Visual Basic o de C# al flujo de trabajo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|Una versión compensable de [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|Una versión compensable de **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Permite llamar al código para deshacer o compensar las operaciones ya realizadas por el flujo de trabajo cuando se produce un error. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Un contenedor para una o varias actividades que realizan la compensación para una actividad TransactionScopeActivity completada [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Ejecuta actividades secundarias basadas en una condición que se aplica a la propia actividad [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) y en función de las condiciones que se aplican por separado a cada elemento secundario. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|Le permite compilar retrasos en el flujo de trabajo, basados en un intervalo de tiempo de espera. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad DelayActivity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Ajusta una o varias actividades que se ejecutan cuando se produce un evento especificado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Proporciona un marco de trabajo para asociar eventos a una actividad. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Ejecuta de forma simultánea su actividad secundaria principal con un [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Se usa para controlar una excepción del tipo especificado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Representa una actividad compuesta que tiene una lista ordenada de actividades secundarias de tipo [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Se usa junto con la actividad [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) para las comunicaciones de entrada y salida con un servicio local. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Prueba una condición en cada bifurcación y realiza actividades en la primera bifurcación para la que la condición es **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Representa una bifurcación de un [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Permite que el flujo de trabajo invoque un servicio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Permite que el flujo de trabajo invoque otro flujo de trabajo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|Una actividad compuesta que solo contiene actividades secundarias de [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad ListenActivity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Proporciona una manera de programar dos o más bifurcaciones de actividades de **SequenceActivity** secundarias para el procesamiento al mismo tiempo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Se usa para representar una colección de reglas. Regla formada por condiciones y las acciones resultantes. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Crea varias instancias de una única actividad secundaria. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Proporciona una manera sencilla de vincular varias actividades para su ejecución secuencial. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Representa un estado en un flujo de trabajo de equipo de estado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Se usa en una actividad [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) como un contenedor para las actividades secundarias que se ejecutan al mantener la actividad **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Se usa en una actividad [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) como contenedor de actividades secundarias que se ejecutan al entrar en la actividad **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Suspende la operación del flujo de trabajo para permitir la intervención si se produce alguna condición de error que requiere atención especial. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Ejecuta secuencialmente las actividades contenidas en un dominio sincronizado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Permite finalizar inmediatamente el funcionamiento del flujo de trabajo si se produce una condición de error. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|Permite capturar excepciones de empresa iniciadas como parte de los metadatos de proceso para un flujo de trabajo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Proporciona un marco de trabajo para transacciones y control de excepciones. Para obtener más información, vea [usar la actividad TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Permite crear el modelo de la instancia de un error de servicio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Recibe los datos de un servicio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Responde a una solicitud de servicio Web realizada a un flujo de trabajo. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Permite que el flujo de trabajo se ejecute en bucle hasta que se cumpla una condición. [!INCLUDE[crdefault](../includes/crdefault-md.md)][mediante la actividad WhileActivity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] cómo crear actividades personalizadas, vea [desarrollar actividades personalizadas](https://go.microsoft.com/fwlink?LinkID=65023) y [usar el diseñador de actividad heredado](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Esta sección
 [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md) Describe las diferentes vistas de diseño de las actividades.

 [Cómo: agregar actividades al cuadro de herramientas (heredado)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Muestra cómo agregar actividades al cuadro de herramientas.

 [Cómo: crear una condición de regla declarativa (heredado)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Muestra los pasos para crear una condición de regla declarativa.

 [Cómo: crear un conjunto de reglas de PolicyActivity (heredado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Muestra los pasos para crear un conjunto de reglas de PolicyActivity.

 [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Muestra los pasos para implementar una operación de contrato de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

 [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Muestra los pasos necesarios para invocar una operación de contrato de [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Vea también
 [Actividades Windows Workflow Foundation](https://go.microsoft.com/fwlink?LinkID=65005) [desarrollar flujos](https://go.microsoft.com/fwlink?LinkID=65010) de trabajo [desarrollar actividades de flujo de trabajo](https://go.microsoft.com/fwlink?LinkID=65023)