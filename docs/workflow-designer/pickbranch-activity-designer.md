---
title: "Diseñador de actividades PickBranch | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be1cb6fdef8eed2a0f6b02f987143220e9b99d91
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="pickbranch-activity-designer"></a>Diseñador de actividades PickBranch
La clase <xref:System.Activities.Statements.PickBranch> proporciona una ruta de acceso basada en eventos de ejecución en una actividad de la clase <xref:System.Activities.Statements.Pick> que un evento de entrada puede desencadenar.

## <a name="pickbranch"></a>PickBranch
 Los objetos <xref:System.Activities.Statements.PickBranch> se encuentran en la colección de la propiedad <xref:System.Activities.Statements.Pick.Branches%2A> de una actividad de la clase <xref:System.Activities.Statements.Pick>. Cada actividad de la clase <xref:System.Activities.Statements.PickBranch> se encuentra en una bifurcación de la actividad de la clase <xref:System.Activities.Statements.Pick> y se puede ejecutar debido a que algún evento de entrada actúa como desencadenador. De esta manera el Diseñador de flujo de trabajo de Windows proporciona el modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick
 El **PickBranch** diseñador puede encontrarse en el **flujo de Control** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas** ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X).

 Dos vacío <xref:System.Activities.Statements.PickBranch> objetos con nombres para mostrar **Branch1** y **Branch2** se crean de forma predeterminada como elementos de un <xref:System.Activities.Statements.Pick> actividad cuando la **elegir** Diseñador de actividad se coloca inicialmente en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Los respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propiedad se pueden editar en el **PickBranch** encabezado del diseñador o en el **propiedades** ventana para cada bifurcación.

 Hay dos maneras de agregar <xref:System.Activities.Statements.PickBranch> objetos a la colección de un <xref:System.Activities.Statements.Pick> objeto: arrastrando y colocando el **PickBranch** diseñador desde el **cuadro de herramientas** o mediante el menú contextual de en el **elegir** superficie de diseño:

1.  El **PickBranch** el diseñador crea un <xref:System.Activities.Statements.PickBranch> cuando se arrastra desde el **cuadro de herramientas** y se coloca en una de las bifurcaciones de un **elegir** Diseñador de actividad en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie. Los nuevos objetos <xref:System.Activities.Statements.PickBranch> se pueden colocar dentro del diseñador <xref:System.Activities.Statements.Pick> a la izquierda o derecha de cualquier elemento <xref:System.Activities.Statements.PickBranch> existente que ya se encuentre en la colección. Al arrastrar un **PickBranch** diseñador en la **elegir** diseñador con el mouse, el **elegir** diseñador utiliza una banda azul grisácea vertical para indicar dónde el <xref:System.Activities.Statements.PickBranch> se agrega a una posición determinada del mouse.

2.  Haga clic en **elegir** Diseñador de actividad (pero no dentro **PickBranch** diseñador) para obtener un menú contextual y seleccione **crear la bifurcación** para agregar un nuevo <xref:System.Activities.Statements.PickBranch>. Tenga en cuenta que la nueva <xref:System.Activities.Statements.PickBranch> se agrega a la derecha de la existente <xref:System.Activities.Statements.PickBranch> objetos en el **elegir** diseñador.

 El **PickBranch** diseñador se puede expandir para que muestre el **desencadenador** y **acción** cuadros o contraídos, haga clic en los corchetes angulares dobles en el lado derecho de sus encabezados. Editar la <xref:System.Activities.Statements.PickBranch.Trigger%2A> y <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> colocando las actividades en el **desencadenador** y **acción** cuadros de sus diseñadores.

 El <xref:System.Activities.Statements.PickBranch> objetos en el <xref:System.Activities.Statements.Pick.Branches%2A> colección de un <xref:System.Activities.Statements.Pick> de objetos, se pueden reordenar arrastrándolas y colocándolas en una ubicación nueva en el **elegir** diseñador. El **elegir** diseñador utiliza una banda azul grisácea vertical para indicar dónde el <xref:System.Activities.Statements.PickBranch> se agrega para una posición determinada del mouse.

 Hay dos formas de eliminar una clase <xref:System.Activities.Statements.PickBranch>:

1.  Seleccione el **PickBranch** diseñador y elimínelo.

2.  Seleccione el **PickBranch** contextual Diseñador, para obtener el menú contextual y seleccione **eliminar**.

 No olvide seleccionar la **PickBranch** diseñador, como seleccionar una de las actividades dentro de su **desencadenador** o **acción** cuadros elimina por error una de esas actividades y no la <xref:System.Activities.Statements.PickBranch> objeto.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propiedades PickBranch en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las propiedades de la clase <xref:System.Activities.Statements.PickBranch> más útiles y se describe cómo se usan en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|El nombre descriptivo que se muestra en el encabezado de la **PickBranch** diseñador. El valor predeterminado es Branch.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una acción <xref:System.Activities.Statements.PickBranch.Trigger%2A> que puede invocar a la propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A> que se ejecuta si se desencadena.|

## <a name="see-also"></a>Vea también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [Actividad Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Uso de la actividad Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)