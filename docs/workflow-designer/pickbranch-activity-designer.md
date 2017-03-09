---
title: "Dise&#241;ador de actividades PickBranch | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades PickBranch
La clase <xref:System.Activities.Statements.PickBranch> proporciona una ruta de acceso basada en eventos de ejecución en una actividad de la clase <xref:System.Activities.Statements.Pick> que un evento de entrada puede desencadenar.  
  
## PickBranch  
 Los objetos <xref:System.Activities.Statements.PickBranch> se encuentran en la colección de la propiedad <xref:System.Activities.Statements.Pick.Branches%2A> de una actividad de la clase <xref:System.Activities.Statements.Pick>.Cada actividad de la clase <xref:System.Activities.Statements.PickBranch> se encuentra en una bifurcación de la actividad de la clase <xref:System.Activities.Statements.Pick> y se puede ejecutar debido a que algún evento de entrada actúa como desencadenador.En este sentido, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona un modelado de flujo de control basado en eventos.Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### Usar el diseñador de actividad Pick  
 El diseñador **PickBranch** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 De forma predeterminada se crean dos objetos <xref:System.Activities.Statements.PickBranch> vacíos con los nombres para mostrar **Branch1** y **Branch2** como elementos de una actividad de la clase <xref:System.Activities.Statements.Pick> cuando el diseñador de actividad **Pick** se coloca inicialmente en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Los respectivos valores de la propiedad <xref:System.Activities.Statements.PickBranch.DisplayName%2A> se pueden editar en el encabezado del diseñador **PickBranch** o en la ventana **Propiedades** para cada bifurcación.  
  
 Hay dos maneras de agregar los objetos <xref:System.Activities.Statements.PickBranch> a la colección de un objeto <xref:System.Activities.Statements.Pick>: arrastrando y colocando el diseñador **PickBranch** desde el **Cuadro de herramientas** o usando el menú contextual desde la superficie de diseño de **Pick**:  
  
1.  El diseñador **PickBranch** crea una clase <xref:System.Activities.Statements.PickBranch> cuando se arrastra desde el **Cuadro de herramientas** y se coloca en una de las bifurcaciones de un diseñador de actividad **Pick** en la superficie del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Los nuevos objetos <xref:System.Activities.Statements.PickBranch> se pueden colocar dentro del diseñador <xref:System.Activities.Statements.Pick> a la izquierda o derecha de cualquier elemento <xref:System.Activities.Statements.PickBranch> existente que ya se encuentre en la colección.Al arrastrar un diseñador **PickBranch** al diseñador **Pick** con un mouse, el diseñador **Pick** usa una banda azul grisácea vertical para indicar donde se agrega la clase <xref:System.Activities.Statements.PickBranch> con respecto a una posición determinada del mouse.  
  
2.  Haga clic con el botón secundario en el diseñador de actividad **Pick** \(pero no dentro del diseñador **PickBranch**\) para obtener un menú contextual y seleccione **Crear la bifurcación** para agregar una clase <xref:System.Activities.Statements.PickBranch> nueva.Observe que la nueva clase <xref:System.Activities.Statements.PickBranch> se agrega a la derecha de los objetos <xref:System.Activities.Statements.PickBranch> existentes en el diseñador **Pick**.  
  
 El diseñador **PickBranch** se puede expandir para que muestre los cuadros **Desencadenador** y **Acción** o contraerse si se hace clic en los símbolos de intercalación dobles situados a la derecha de sus encabezados.Edite las propiedades <xref:System.Activities.Statements.PickBranch.Trigger%2A> y <xref:System.Activities.Statements.PickBranch.Action%2A> de cada clase <xref:System.Activities.Statements.PickBranch> colocando las actividades en los cuadros **Desencadenador** y **Acción** de sus diseñadores.  
  
 Los objetos <xref:System.Activities.Statements.PickBranch> en la colección <xref:System.Activities.Statements.Pick.Branches%2A> de un objeto <xref:System.Activities.Statements.Pick>, se puede reordenar si se arrastran y colocan en una ubicación nueva en el diseñador **Pick**.El diseñador **Pick** utiliza una banda azul grisácea vertical para indicar dónde se agrega <xref:System.Activities.Statements.PickBranch> con respecto a una ubicación del mouse determinada.  
  
 Hay dos formas de eliminar una clase <xref:System.Activities.Statements.PickBranch>:  
  
1.  Seleccione el diseñador **PickBranch** y elimínelo.  
  
2.  Seleccione el diseñador **PickBranch**, haga clic con el botón secundario del mouse para que aparezca el menú contextual y seleccione **Eliminar**.  
  
 Asegúrese de seleccionar el diseñador **PickBranch**, ya que si selecciona una de las actividades en sus cuadros **Desencadenador** o **Acción** por equivocación, se elimina una de esas actividades y no el objeto <xref:System.Activities.Statements.PickBranch>.  
  
### Propiedades PickBranch en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de la clase <xref:System.Activities.Statements.PickBranch> más útiles y se describe cómo se usan en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|El nombre descriptivo que se muestra en el encabezado del diseñador **PickBranch**.El valor predeterminado es Branch.<br /><br /> Aunque el valor de propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una acción <xref:System.Activities.Statements.PickBranch.Trigger%2A> que puede invocar a la propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A> que se ejecuta si se desencadena.|  
  
## Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)   
 [Actividad Pick](../Topic/Pick%20Activity.md)   
 [Uso de la actividad Pick](../Topic/Using%20the%20Pick%20Activity.md)