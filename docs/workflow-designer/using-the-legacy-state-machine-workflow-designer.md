---
title: "Usar el dise&#241;ador de flujo de trabajo de m&#225;quina de estados heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "EventDrivenActivity, actividad"
  - "Actividad SetStateActivity"
  - "diseñador de flujo de trabajo de máquina de estados"
  - "flujos de trabajo de equipos de estado, actividades"
  - "flujos de trabajo de equipos de estado, diseñador"
  - "Actividad StateActivity"
  - "Actividad StateFinalizationActivity"
  - "Actividad StateInitializationActivity"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Usar el dise&#241;ador de flujo de trabajo de m&#225;quina de estados heredado
Cuando crea un nuevo proyecto de flujo de trabajo de máquina de estados en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], puede optar por usar las plantillas de proyecto **Aplicación de consola de flujos de trabajo de equipo de estado** o **Biblioteca de flujos de trabajo de equipo de estado** heredadas.Si elige una de estas plantillas de proyecto de máquina de estados, el diseñador de máquina de estados se presenta como la interfaz de usuario del diseñador de flujo de trabajo heredada.Para obtener información sobre las plantillas de proyecto de máquina de estados heredadas, vea [Cómo: Crear aplicaciones de consola de flujos de trabajo de equipo de estado \(Heredado\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md) y [Cómo: Crear un biblioteca de flujos de trabajo de equipo de estado \(Heredado\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md).  
  
 Un flujo de trabajo de máquina de estados está compuesto por un conjunto de estados.Se designa un estado como estado inicial.Cada estado puede recibir un conjunto de eventos determinado.En función de un evento, se puede realizar una transición a otro estado.El flujo de trabajo de equipo de estado puede tener un estado final.Cuando se realiza una transición al estado final, el flujo de trabajo termina.  
  
## Vistas del diseñador de equipo de estado  
 El diseñador de equipo de estado es un diseñador de forma libre, lo que significa que las actividades se pueden mover libremente por la superficie de diseño.El diseñador de equipo de estado tiene dos vistas: las vistas *estado* y *orientada a eventos*.  
  
 La vista de estado muestra las actividades de estado y las actividades orientadas a eventos que pueden estar dentro de una actividad de estado.En esta vista, las transiciones de un estado a otro se representan mediante líneas que van de la actividad orientada a eventos en un estado a otro estado.También puede crear las transiciones dibujando la línea usted mismo.Para dibujar la transición, seleccione la actividad orientada a eventos y, a continuación, seleccione uno de los controladores de la actividad y arrástrelo.Esta acción dibuja una línea.A continuación, la línea se adjunta al estado de destino, lo que indica una transición entre estados.  
  
 Para tener acceso a la vista orientada a eventos, haga doble clic en una actividad orientada a eventos.El diseñador que aparece es muy parecido al diseñador de flujo de trabajo secuencial.En la parte superior del diseñador, una barra de exploración muestra la jerarquía de las actividades hasta la actividad orientada a eventos que se aparece.Puede volver a la vista de estado haciendo clic en cualquier elemento de la jerarquía que se muestra.Si ha dibujado una transición de un estado a otro en la vista de estado, y si está en la vista orientada a eventos de esa actividad, se agrega una actividad de estado fija a la actividad orientada a eventos.Si cambia las propiedades de la actividad de estado fija, el cambio queda reflejado en la vista de estado.  
  
## Actividades de flujo de trabajo de equipo de estado  
 En la tabla siguiente se describen las actividades principales que se utilizan en un diseñador de flujo de trabajo de máquina de estados.  
  
|Nombre del cuadro de herramientas|Actividad|Descripción|  
|---------------------------------------|---------------|-----------------|  
|**Estado**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa un estado de una máquina de estado; puede contener actividades **StateActivity** adicionales.Para obtener más información, vea [Usar la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado.Para obtener más información, vea [Usar la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Se ejecuta cuando se entra en un estado; puede contener otras actividades.Para obtener más información, vea [Usar la actividad StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Ejecuta las actividades que contiene al salir de una actividad [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042).Para obtener más información, vea [Usar la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Se utiliza para los estados que dependen de un evento externo para empezar a ejecutarse.La actividad **EventDrivenActivity** debe tener una actividad que implemente la interfaz [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) como primera actividad secundaria.Para obtener más información, vea [Usar la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 El componente principal de un flujo de trabajo de equipo de estado es la actividad [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042).Al capturarse eventos en diversos puntos en un flujo de trabajo de equipo de estado, se entra en estados diferentes para administrar las tareas asociadas a los eventos.Durante la duración del flujo de trabajo, éste puede entrar en y salir de varios estados diferentes.Estos estados conectan entre sí utilizando la actividad [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041).  
  
 Al arrastrar una nueva **StateActivity** a la superficie de diseño de flujo de trabajo, puede agregar las actividades [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), o bien actividades **StateActivity** como actividades secundarias.  
  
> [!CAUTION]
>  Al utilizar el diseñador de flujo de trabajo de máquina de estados para crear flujos de trabajo, debe supervisar la estructura del flujo de trabajo que está diseñando con la ventana de la vista **Esquema del documento**.La vista de la estructura del flujo de trabajo de equipo de estado en la ventana de la vista **Esquema del documento** refleja el diseño lógico de las actividades del archivo de marcado del flujo de trabajo.El diseño físico de las actividades de flujo de trabajo tal como aparecen en la superficie de diseño podría no reflejar el diseño lógico de las actividades del archivo de marcado del flujo de trabajo.  
>   
>  Para abrir la ventana **Esquema del documento**, en el menú **Ver**, seleccione **Otras ventanas** y, a continuación, seleccione **Esquema del documento**.  
  
## Vea también  
 [Cómo: Crear aplicaciones de consola de flujos de trabajo de equipo de estado \(Heredado\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)   
 [Cómo: Crear un biblioteca de flujos de trabajo de equipo de estado \(Heredado\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)   
 [Flujos de trabajo de máquina de estados](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Uso de la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Uso de la actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Uso de la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Uso de la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Uso de la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)