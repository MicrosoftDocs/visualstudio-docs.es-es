---
title: "Dise&#241;ador de actividades Pick | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades Pick
La actividad <xref:System.Activities.Statements.Pick> proporciona un flujo de control basado en eventos.La actividad ejecuta una de las diversas bifurcaciones en respuesta a un evento desencadenador.  
  
## Actividad Pick  
 Una actividad <xref:System.Activities.Statements.Pick> contiene una colección de objetos <xref:System.Activities.Statements.PickBranch>, uno de los cuales puede ejecutar la actividad <xref:System.Activities.Statements.Pick> a causa de algún evento de entrada que actúa como un desencadenador.De esta forma, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona un modelado de flujo de control basado en eventos.Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>.Al comienzo de una ejecución de la actividad <xref:System.Activities.Statements.Pick>, se programan todas las actividades de desencadenador de los elementos <xref:System.Activities.Statements.PickBranch>.Cuando se completa la primera actividad, se programa la actividad de acción correspondiente y el resto de actividades de desencadenador se cancelan.  
  
### Utilizar el diseñador de actividades Pick  
 El diseñador de actividades **Pick** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **Pick** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente los diseñadores de actividades, por ejemplo, en un diseñador de actividades **Sequence**.Después de colocarlo en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], crea una actividad <xref:System.Activities.Statements.Pick> que, de forma predeterminada, contiene dos actividades <xref:System.Activities.Statements.PickBranch> vacías como elementos, con los nombres para mostrar Branch1 y Branch2.Estos valores de propiedad <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectivos se pueden editar en el encabezado del diseñador de actividades **PickBranch** o dentro de la ventana **Propiedades** para cada bifurcación.  
  
 Hay dos maneras de agregar las actividades <xref:System.Activities.Statements.PickBranch> a la colección de un objeto <xref:System.Activities.Statements.Pick>: arrastrando y colocando el diseñador **PickBranch** desde el **Cuadro de herramientas** o utilizando el menú contextual desde la superficie de diseño **Pick**.Para obtener información detallada, vea el tema [PickBranch](../workflow-designer/pickbranch-activity-designer.md).Observe que el único elemento que se puede colocar dentro de un diseñador de actividades **Pick** es un diseñador de actividades **PickBranch**.  
  
### Propiedades de la actividad Pick en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Pick> y se describe cómo se usan en el diseñador.Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Pick> en el encabezado.El valor predeterminado es Pick.El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
  
## Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)   
 [Actividad Pick](../Topic/Pick%20Activity.md)   
 [Uso de la actividad Pick](../Topic/Using%20the%20Pick%20Activity.md)