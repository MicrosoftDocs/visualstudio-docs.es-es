---
title: "Dise&#241;adores de actividad de transici&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "sdanie"
manager: "erikre"
---
# Dise&#241;adores de actividad de transici&#243;n
<xref:System.Activities.Statements.Transition> representa la transición entre dos estados.  
  
## Usar el diseñador de actividades Transition  
 El diseñador de actividad de transición permite configurar una transición entre dos estados.  
  
### Propiedades de Transition en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Transition> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Transition>.El valor predeterminado es **T1**.El valor se puede editar en la cuadrícula de propiedades, en el encabezado del diseñador expandido de la transición y en el encabezado de la sección de acción desde el diseñador expandido de la transición.<xref:System.Activities.Activity.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Si está presente, especifica una expresión que se debe evaluar como **True** antes de que el control se pase al estado de destino.Esta condición se puede editar en la cuadrícula de propiedades y en el diseñador expandido de transición.Varias condiciones en una transición compartida se evalúan en el orden en que aparecen en el diseñador de la transición. **Note:**  Tenga en cuenta que si la condición <xref:System.Activities.Statements.Transition.Condition%2A> de una transición se evalúa en **False** \(o todas las condiciones de una transición de desencadenador compartido se evalúan en **False**\), la transición no se producirá y se reprogramarán todos los desencadenadores para todas las transiciones desde el estado.En este tutorial, no puede suceder esta situación debido a la forma en que están configuradas las condiciones \(tenemos acciones específicas para determinar si el supuesto es correcto o incorrecto\).|  
|**Origen**|True|Indica el estado del que esta transición se origina.Al hacer clic en el nombre del estado de origen se cambia la vista de diseñador a una vista expandida de ese estado.Se establece este valor cuando la transición se crea y no se puede cambiar.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Especifica la actividad cuya finalización inicia la transición.Para establecer esta actividad, arrastre una actividad del **Cuadro de herramientas** y colóquela sobre la sección **Desencadenador** de la transición.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Especifica la actividad que se ejecuta cuando la actividad desencadenadora se completa y <xref:System.Activities.Statements.Transition.Condition%2A>, si está presente, se evalúa como **true**.Se ejecuta esta actividad en la transición al estado de destino, después de que la actividad <xref:System.Activities.Statements.State.Exit%2A> para el estado de origen, si existe, se ejecute.Cuando el diseñador de transición se expande, este valor se puede establecer arrastrando una actividad del **Cuadro de herramientas** y colocándola sobre la sección **Acción** de la transición.Puede haber varias acciones para una única transición.Las acciones individuales se pueden expandir y contraer, y se pueden ordenar haciendo clic en la flecha arriba o abajo que aparece en la acción cuando hay varias acciones en una transición.|  
|**Destination**|True|Indica el estado al que cambia la máquina de estados después de que la transición se complete.Esto corresponde a la propiedad <xref:System.Activities.Statements.Transition.To%2A> de la transición en el modelo de objetos.Al hacer clic en el nombre del estado de destino se cambia la vista de diseñador a una vista expandida de ese estado.Se establece este valor cuando la transición se crea y se puede cambiar arrastrando la flecha que conecta la transición al estado de destino en el diseñador.|  
  
### Crear transiciones  
 Las transiciones se crean arrastrando una línea desde un estado a otro o colocando un estado sobre los triángulos que aparecen cuando se arrastra un estado a otro estado.Para crear una transición arrastrando, mantenga el mouse sobre el borde del estado de origen y arrastre una línea desde el estado de origen al estado de destino.Para crear una transición mediante colocación, arrastrar el estado de destino y mantenga el mouse sobre el estado de origen, y colóquela sobre uno de los cuatro triángulos que aparecen alrededor del estado de origen.El estado de destino puede ser un nuevo estado arrastrado desde el **Cuadro de herramientas** o un estado existente arrastrado desde el diseñador de flujo de trabajo.  
  
> [!NOTE]
>  Un solo estado en una máquina de estados puede tener hasta 76 transiciones creadas con el diseñador de flujo de trabajo.El límite de transiciones para un estado para los flujos de trabajo creados fuera del diseñador está limitado por los recursos del sistema.  
  
 Las transiciones compartidas de desencadenador son el conjunto de transiciones que comparten el mismo evento desencadenador.Un desencadenador compartido permite la progresión condicional a un estado de destino basándose en la evaluación de expresiones configuradas para varias transiciones que comparten un evento desencadenador de común.Para agregar acciones adicionales a una transición y crear una transición compartida, haga clic en el círculo que indica el inicio de la transición deseada y arrástrelo hasta el estado deseado.La nueva transición compartirá un mismo desencadenador que la transición inicial, pero tendrá una condición y una acción únicas.Las transiciones compartidas también se pueden crear desde el diseñador de transición haciendo clic en **Agregar transición de desencadenador compartida** en la parte inferior del diseñador de transición y seleccionando el estado del destino deseada en la lista desplegable **Estados disponibles para conectar**.  
  
## Vea también  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)