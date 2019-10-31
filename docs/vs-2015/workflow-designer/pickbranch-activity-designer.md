---
title: Diseñador de actividades PickBranch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7c70aa8282fb8f50ed6faca5bcee3177ef81e15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672582"
---
# <a name="pickbranch-activity-designer"></a>Diseñador de actividades PickBranch
La clase <xref:System.Activities.Statements.PickBranch> proporciona una ruta de acceso basada en eventos de ejecución en una actividad de la clase <xref:System.Activities.Statements.Pick> que un evento de entrada puede desencadenar.

## <a name="pickbranch"></a>PickBranch
 Los objetos <xref:System.Activities.Statements.PickBranch> se encuentran en la colección de la propiedad <xref:System.Activities.Statements.Pick.Branches%2A> de una actividad de la clase <xref:System.Activities.Statements.Pick>. Cada actividad de la clase <xref:System.Activities.Statements.PickBranch> se encuentra en una bifurcación de la actividad de la clase <xref:System.Activities.Statements.Pick> y se puede ejecutar debido a que algún evento de entrada actúa como desencadenador. En este sentido, [!INCLUDE[wfd1](../includes/wfd1-md.md)] proporciona un modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick
 El diseñador de **PickBranch** se puede encontrar en la categoría **flujo de control** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 De forma predeterminada, se crean dos objetos <xref:System.Activities.Statements.PickBranch> vacíos con los nombres para mostrar de **BRANCH1** y **Branch2** como elementos de una actividad <xref:System.Activities.Statements.Pick> cuando el diseñador de actividad **Pick** se coloca inicialmente en el [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Estos valores de propiedad de <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectivos se pueden editar en el encabezado del diseñador de **PickBranch** o en la ventana **propiedades** para cada bifurcación.

 Hay dos maneras de agregar objetos <xref:System.Activities.Statements.PickBranch> a la colección de un objeto <xref:System.Activities.Statements.Pick>: arrastrar y colocar el diseñador **PickBranch** desde el cuadro de **herramientas** o mediante el menú contextual desde la superficie de diseño de **Pick** :

1. El diseñador **PickBranch** crea un <xref:System.Activities.Statements.PickBranch> cuando se arrastra desde el cuadro de **herramientas** y se coloca en una de las bifurcaciones de un diseñador de actividad **Pick** en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Los nuevos objetos <xref:System.Activities.Statements.PickBranch> se pueden colocar dentro del diseñador <xref:System.Activities.Statements.Pick> a la izquierda o derecha de cualquier elemento <xref:System.Activities.Statements.PickBranch> existente que ya se encuentre en la colección. Al arrastrar un diseñador **PickBranch** al diseñador **Pick** con un mouse, el diseñador **Pick** utiliza una banda azul-gris vertical para indicar dónde se agrega el <xref:System.Activities.Statements.PickBranch> para una ubicación determinada del mouse.

2. Haga clic con el botón derecho en el diseñador de actividades **Pick** (pero no dentro del diseñador **PickBranch** ) para obtener un menú contextual y seleccione **crear rama** para agregar una nueva <xref:System.Activities.Statements.PickBranch>. Observe que el nuevo <xref:System.Activities.Statements.PickBranch> se agrega a la derecha de los objetos <xref:System.Activities.Statements.PickBranch> existentes en el diseñador **Pick** .

   El diseñador de **PickBranch** se puede expandir para mostrar los cuadros de **desencadenador** y **acción** o contraerlo haciendo clic en los dobles acentos en el lado derecho de sus encabezados. Edite el <xref:System.Activities.Statements.PickBranch.Trigger%2A> y <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> colocando las actividades en los cuadros **desencadenador** y **acción** de sus diseñadores.

   Los objetos <xref:System.Activities.Statements.PickBranch> de la colección <xref:System.Activities.Statements.Pick.Branches%2A> de un objeto <xref:System.Activities.Statements.Pick>, se pueden reordenar arrastrándolos y colocándolos en una nueva ubicación dentro del diseñador **Pick** . El diseñador **Pick** utiliza una banda azul-gris vertical para indicar dónde se agrega el <xref:System.Activities.Statements.PickBranch> para una ubicación determinada del mouse.

   Hay dos formas de eliminar una clase <xref:System.Activities.Statements.PickBranch>:

3. Seleccione el diseñador de **PickBranch** y elimínelo.

4. Seleccione el diseñador **PickBranch** , haga clic con el botón derecho para obtener el menú contextual y seleccione **eliminar**.

   Asegúrese de seleccionar el diseñador **PickBranch** , ya que si selecciona una de las actividades en sus cuadros **desencadenador** o **acción** por equivocación, se eliminará una de esas actividades y no el objeto <xref:System.Activities.Statements.PickBranch>.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propiedades PickBranch en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las propiedades de la clase <xref:System.Activities.Statements.PickBranch> más útiles y se describe cómo se usan en el [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nombre descriptivo que se muestra en el encabezado del diseñador **PickBranch** . El valor predeterminado es Branch.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una acción <xref:System.Activities.Statements.PickBranch.Trigger%2A> que puede invocar a la propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A> que se ejecuta si se desencadena.|

## <a name="see-also"></a>Vea también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) [Selección de actividades](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e) [Uso de la actividad de selección](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)