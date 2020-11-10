---
title: Diseñador de actividades Diseñador de flujo de trabajo-PickBranch
description: Obtenga información sobre cómo el diseñador de actividades PickBranch proporciona una ruta de acceso basada en eventos de ejecución dentro de una actividad Pick que se puede desencadenar mediante un evento de entrada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bce1cee7fad7ccff57a6911c99a9470a22b9a927
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434238"
---
# <a name="pickbranch-activity-designer"></a>Diseñador de actividades PickBranch

La clase <xref:System.Activities.Statements.PickBranch> proporciona una ruta de acceso basada en eventos de ejecución en una actividad de la clase <xref:System.Activities.Statements.Pick> que un evento de entrada puede desencadenar.

## <a name="pickbranch"></a>PickBranch

Los objetos <xref:System.Activities.Statements.PickBranch> se encuentran en la colección de la propiedad <xref:System.Activities.Statements.Pick.Branches%2A> de una actividad de la clase <xref:System.Activities.Statements.Pick>. Cada actividad de la clase <xref:System.Activities.Statements.PickBranch> se encuentra en una bifurcación de la actividad de la clase <xref:System.Activities.Statements.Pick> y se puede ejecutar debido a que algún evento de entrada actúa como desencadenador. De este modo, el Diseñador de flujo de trabajo proporciona modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick

Acceda al diseñador de **PickBranch** en la categoría **flujo de control** del **cuadro de herramientas**.

De <xref:System.Activities.Statements.PickBranch> forma predeterminada, se crean dos objetos vacíos con los nombres para mostrar de **BRANCH1** y **Branch2** como elementos de una <xref:System.Activities.Statements.Pick> actividad cuando el diseñador de actividad **Pick** se coloca inicialmente en el diseñador de flujo de trabajo. Estos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propiedad respectivos se pueden editar en el encabezado del diseñador de **PickBranch** o en la ventana **propiedades** para cada bifurcación.

Hay dos maneras de agregar <xref:System.Activities.Statements.PickBranch> objetos a la colección de un <xref:System.Activities.Statements.Pick> objeto: arrastrar y colocar el diseñador de **PickBranch** desde el **cuadro de herramientas** o mediante el menú contextual desde la superficie de diseño de **Pick** :

- El diseñador de **PickBranch** crea un <xref:System.Activities.Statements.PickBranch> cuando se arrastra desde el **cuadro de herramientas** y se coloca en una de las bifurcaciones de un diseñador de actividad **Pick** en la superficie diseñador de flujo de trabajo. Los nuevos objetos <xref:System.Activities.Statements.PickBranch> se pueden colocar dentro del diseñador <xref:System.Activities.Statements.Pick> a la izquierda o derecha de cualquier elemento <xref:System.Activities.Statements.PickBranch> existente que ya se encuentre en la colección. Al arrastrar un diseñador **PickBranch** al diseñador **Pick** con un mouse, el diseñador **Pick** utiliza una banda azul-gris vertical para indicar dónde <xref:System.Activities.Statements.PickBranch> se agrega para una ubicación del mouse determinada.

- Haga clic con el botón secundario en el diseñador de actividades **Pick** (pero no dentro del diseñador **PickBranch** ) para obtener un menú contextual y seleccione **crear rama** para agregar un nuevo <xref:System.Activities.Statements.PickBranch> . Tenga en cuenta que la nueva <xref:System.Activities.Statements.PickBranch> se agrega a la derecha de los <xref:System.Activities.Statements.PickBranch> objetos existentes en el diseñador **Pick** .

El diseñador de **PickBranch** se puede expandir para mostrar los cuadros de **desencadenador** y **acción** o contraerlo haciendo clic en los dobles acentos en el lado derecho de sus encabezados. Edite <xref:System.Activities.Statements.PickBranch.Trigger%2A> y <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> colocando las actividades en los cuadros **desencadenador** y **acción** de sus diseñadores.

Los <xref:System.Activities.Statements.PickBranch> objetos de la <xref:System.Activities.Statements.Pick.Branches%2A> colección de un <xref:System.Activities.Statements.Pick> objeto, se pueden reordenar arrastrándolos y colocándolos en una nueva ubicación dentro del diseñador **Pick** . El diseñador **Pick** utiliza una banda azul-gris vertical para indicar dónde <xref:System.Activities.Statements.PickBranch> se agrega para una ubicación del mouse determinada.

Hay dos formas de eliminar una clase <xref:System.Activities.Statements.PickBranch>:

- Seleccione el diseñador de **PickBranch** y elimínelo.
- Seleccione el diseñador **PickBranch** , haga clic con el botón derecho para obtener el menú contextual y seleccione **eliminar**.

Asegúrese de seleccionar el diseñador **PickBranch** , ya que si selecciona una de las actividades en sus cuadros **desencadenador** o **acción** por equivocación, se eliminará una de esas actividades y no el <xref:System.Activities.Statements.PickBranch> objeto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propiedades PickBranch en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las <xref:System.Activities.Statements.PickBranch> propiedades más útiles y se describe cómo utilizarlas en el diseñador de flujo de trabajo.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|Falso|Nombre descriptivo que se muestra en el encabezado del diseñador **PickBranch** . El valor predeterminado es Branch.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una acción <xref:System.Activities.Statements.PickBranch.Trigger%2A> que puede invocar a la propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|Falso|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A> que se ejecuta si se desencadena.|

## <a name="see-also"></a>Consulte también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [Actividad Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso de la actividad Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)