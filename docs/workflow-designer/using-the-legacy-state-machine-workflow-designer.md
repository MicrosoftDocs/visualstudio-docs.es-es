---
title: Diseñador de flujo de trabajo - mediante el Diseñador de flujo de trabajo de máquina de Estados heredado
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6ad09c2e999d9432b3c4e1062cb3031eb20ff56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Usar el diseñador de flujo de trabajo de máquina de estados heredado

Cuando se crea un nuevo proyecto de flujo de trabajo de máquina de estado en Visual Studio 2010 que tenga como destino la versión 3.5 de .NET Framework o el conocido como WinFX, puede elegir utilizar el **aplicación de consola de flujo de trabajo de equipo de estado** o la  **Biblioteca de flujo de trabajo de máquina de estado** plantilla de proyecto heredado. Si elige una de estas plantillas de proyecto de máquina de estados, el diseñador de máquina de estados se presenta como la interfaz de usuario del diseñador de flujo de trabajo heredada. Para obtener información acerca de las plantillas de proyecto de la máquina de Estados heredados, consulte [Cómo: crear estado de flujo de trabajo de aplicaciones de consola equipo (heredado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) y [Cómo: crear una biblioteca de flujo de trabajo de equipo de estado (heredado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

Un flujo de trabajo de equipo de estado está compuesto por un conjunto de estados. Se designa un estado como estado inicial. Cada estado puede recibir un conjunto de eventos determinado. En función de un evento, se puede realizar una transición a otro estado. El flujo de trabajo de equipo de estado puede tener un estado final. Cuando se realiza una transición al estado final, el flujo de trabajo termina.

## <a name="state-machine-designer-views"></a>Vistas del diseñador de equipo de estado
 El diseñador de equipo de estado es un diseñador de forma libre, lo que significa que las actividades se pueden mover libremente por la superficie de diseño. El Diseñador de máquina de Estados tiene dos vistas: *estado* vista y *orientada a eventos* vista.

 La vista de estado muestra las actividades de estado y las actividades orientadas a eventos que pueden estar dentro de una actividad de estado. En esta vista, las transiciones de un estado a otro se representan mediante líneas que van de la actividad orientada a eventos en un estado a otro estado. También puede crear las transiciones dibujando la línea usted mismo. Para dibujar la transición, seleccione la actividad orientada a eventos y, a continuación, seleccione uno de los controladores de la actividad y arrástrelo. Esta acción dibuja una línea. A continuación, la línea se adjunta al estado de destino, lo que indica una transición entre estados.

 Para tener acceso a la vista orientada a eventos, haga doble clic en una actividad orientada a eventos. El diseñador que aparece es muy parecido al diseñador de flujo de trabajo secuencial. En la parte superior del diseñador, una barra de exploración muestra la jerarquía de las actividades hasta la actividad orientada a eventos que se aparece. Puede volver a la vista de estado haciendo clic en cualquier elemento de la jerarquía que se muestra. Si ha dibujado una transición de un estado a otro en la vista de estado, y si está en la vista orientada a eventos de esa actividad, se agrega una actividad de estado fija a la actividad orientada a eventos. Si cambia las propiedades de la actividad de estado fija, el cambio queda reflejado en la vista de estado.

## <a name="state-machine-workflow-activities"></a>Actividades de flujo de trabajo de equipo de estado
 En la tabla siguiente se describen las actividades principales que se utilizan en un diseñador de flujo de trabajo de máquina de estados.

|Nombre del cuadro de herramientas|Actividad|Descripción|
|------------------|--------------|-----------------|
|**Estado**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa un estado en una máquina de Estados; puede contener adicionales **StateActivity** actividades. Para obtener más información, consulte [mediante la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica una transición a un nuevo estado. Para obtener más información, consulte [mediante la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Se ejecuta cuando se entra en un estado; puede contener otras actividades. Para obtener más información, consulte [mediante la actividad StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Ejecuta actividades contenidas al salir de un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) actividad. Para obtener más información, consulte [mediante la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Se utiliza para los estados que dependen de un evento externo para empezar a ejecutarse. El **EventDrivenActivity** actividad debe tener una actividad que implemente la [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interfaz como la primera actividad secundaria. Para obtener más información, consulte [mediante la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 El componente principal de un flujo de trabajo de máquina de Estados es el [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) actividad. Al capturarse eventos en diversos puntos en un flujo de trabajo de equipo de estado, se entra en estados diferentes para administrar las tareas asociadas a los eventos. Durante la duración del flujo de trabajo, éste puede entrar en y salir de varios estados diferentes. Estos estados se conectan entre sí mediante el uso de la [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) actividad.

 Cuando se arrastra un nuevo **StateActivity** a la superficie de diseño de flujo de trabajo, puede agregar [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), o adicional **StateActivity** actividades como actividades secundarias.

> [!CAUTION]
> Cuando usa el Diseñador de flujo de trabajo de máquina de Estados para crear flujos de trabajo, debe supervisar la estructura del flujo de trabajo que está diseñando con la **esquema del documento** ventana de vista. La vista de la estructura del flujo de trabajo de máquina de estado en el **esquema del documento** vista ventana refleja el diseño lógico de las actividades en el archivo de marcado de flujo de trabajo. El diseño físico de las actividades de flujo de trabajo tal como aparecen en la superficie de diseño podría no reflejar el diseño lógico de las actividades del archivo de marcado del flujo de trabajo.
>
> Para abrir el **esquema del documento** ventana, en la **vista** menú, elija **otras ventanas**y, a continuación, seleccione **esquema del documento**.

## <a name="see-also"></a>Vea también

- [Cómo: Crear aplicaciones de consola de flujos de trabajo de máquina de estados (heredado)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)
- [Cómo: Crear una biblioteca de flujos de trabajo de máquina de estados (heredado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)
- [Flujos de trabajo de equipos de estado](http://go.microsoft.com/fwlink?LinkID=65016)
- [Uso de la actividad StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)
- [Uso de la actividad StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)
- [Uso de la actividad StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)
- [Uso de la actividad SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)
- [Uso de la actividad EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)