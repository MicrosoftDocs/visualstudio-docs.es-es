---
title: Diseñador de flujo de trabajo - Diseñador de actividad PickBranch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6c452cb4fd5b8a343473204c2b2bee614383ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63003650"
---
# <a name="pickbranch-activity-designer"></a>Diseñador de actividades PickBranch

La clase <xref:System.Activities.Statements.PickBranch> proporciona una ruta de acceso basada en eventos de ejecución en una actividad de la clase <xref:System.Activities.Statements.Pick> que un evento de entrada puede desencadenar.

## <a name="pickbranch"></a>PickBranch

Los objetos <xref:System.Activities.Statements.PickBranch> se encuentran en la colección de la propiedad <xref:System.Activities.Statements.Pick.Branches%2A> de una actividad de la clase <xref:System.Activities.Statements.Pick>. Cada actividad de la clase <xref:System.Activities.Statements.PickBranch> se encuentra en una bifurcación de la actividad de la clase <xref:System.Activities.Statements.Pick> y se puede ejecutar debido a que algún evento de entrada actúa como desencadenador. De este modo, el Diseñador de flujo de trabajo proporciona modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick

Acceso a la **PickBranch** diseñador en la **flujo de Control** categoría de la **cuadro de herramientas**.

Dos vacío <xref:System.Activities.Statements.PickBranch> objetos con los nombres para mostrar **Branch1** y **Branch2** se crean de forma predeterminada como elementos de un <xref:System.Activities.Statements.Pick> actividad cuando la **elegir** Diseñador de actividad se coloca inicialmente en el Diseñador de flujo de trabajo. Los respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> se pueden editar los valores de propiedad en el **PickBranch** encabezado del diseñador o dentro del **propiedades** ventana para cada bifurcación.

Hay dos maneras de agregar <xref:System.Activities.Statements.PickBranch> objetos a la colección de un <xref:System.Activities.Statements.Pick> objeto: arrastrando y colocando el **PickBranch** diseñador desde el **cuadro de herramientas**, o mediante el menú contextual de dentro de la **elegir** superficie de diseño:

- El **PickBranch** el diseñador crea un <xref:System.Activities.Statements.PickBranch> cuando se arrastra desde el **cuadro de herramientas** y coloca en una de las bifurcaciones de un **elegir** Diseñador de actividad en el Superficie del Diseñador de flujo de trabajo. Los nuevos objetos <xref:System.Activities.Statements.PickBranch> se pueden colocar dentro del diseñador <xref:System.Activities.Statements.Pick> a la izquierda o derecha de cualquier elemento <xref:System.Activities.Statements.PickBranch> existente que ya se encuentre en la colección. Al arrastrar un **PickBranch** diseñador la **elegir** diseñador con un mouse, el **elegir** diseñador utiliza una banda azul grisáceo vertical para indicar dónde el <xref:System.Activities.Statements.PickBranch> se agrega una posición determinada del mouse.

- Haga clic en **elegir** Diseñador de actividad (pero no dentro **PickBranch** designer) para obtener un menú contextual y seleccione **crear rama** para agregar un nuevo <xref:System.Activities.Statements.PickBranch>. Tenga en cuenta que el nuevo <xref:System.Activities.Statements.PickBranch> se agrega a la derecha de la existente <xref:System.Activities.Statements.PickBranch> objetos en el **elegir** diseñador.

El **PickBranch** diseñador se puede expandir para mostrar el **desencadenador** y **acción** cuadros o contraído, haga clic en los corchetes angulares dobles en el lado derecho de sus encabezados. Editar el <xref:System.Activities.Statements.PickBranch.Trigger%2A> y <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> colocando las actividades en el **desencadenador** y **acción** cuadros de sus diseñadores.

El <xref:System.Activities.Statements.PickBranch> objetos en el <xref:System.Activities.Statements.Pick.Branches%2A> colección de un <xref:System.Activities.Statements.Pick> de objetos, se pueden reordenar arrastrándolos y colocándolos en una nueva ubicación dentro de la **elegir** diseñador. El **elegir** diseñador utiliza una banda azul grisáceo vertical para indicar dónde el <xref:System.Activities.Statements.PickBranch> se agrega una posición determinada del mouse.

Hay dos formas de eliminar una clase <xref:System.Activities.Statements.PickBranch>:

- Seleccione el **PickBranch** diseñador y elimínelo.
- Seleccione el **PickBranch** diseñador, con el botón secundario para obtener el menú contextual y seleccione **eliminar**.

No olvide seleccionar la **PickBranch** diseñador, ya que si selecciona una de las actividades dentro de su **desencadenador** o **acción** cuadros por equivocación, una de esas actividades y no la <xref:System.Activities.Statements.PickBranch> objeto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propiedades PickBranch en el Diseñador de flujo de trabajo

La tabla siguiente muestran los más útiles <xref:System.Activities.Statements.PickBranch> propiedades y se describe cómo se usan en el Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|El nombre descriptivo que se muestra en el encabezado de la **PickBranch** diseñador. El valor predeterminado es Branch.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una acción <xref:System.Activities.Statements.PickBranch.Trigger%2A> que puede invocar a la propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A> que se ejecuta si se desencadena.|

## <a name="see-also"></a>Vea también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [Actividad Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso de la actividad Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)