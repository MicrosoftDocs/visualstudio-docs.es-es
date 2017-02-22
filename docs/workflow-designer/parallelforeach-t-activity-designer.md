---
title: "Dise&#241;ador de actividades ParallelForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades ParallelForEach&lt;T&gt;
La actividad <xref:System.Activities.Statements.ParallelForEach%601> enumera los elementos de una colección y ejecuta una instrucción incrustada para cada elemento de la colección en paralelo, la cual se presenta de forma asincrónica en el mismo subproceso.Utilice esta actividad de control de flujo en lugar de la actividad <xref:System.Activities.Statements.Sequence> si se desea que las actividades secundarias de esta actividad pasen a estado inactivo.  
  
 La actividad <xref:System.Activities.Statements.ParallelForEach%601> tiene una propiedad <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> que contiene a una expresión [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] especificada por el usuario.La actividad <xref:System.Activities.Statements.ParallelForEach%601> evalúa esta propiedad una vez se complete cada bifurcación.Si se evalúa como **true**, la actividad <xref:System.Activities.Statements.ParallelForEach%601> se completa sin ejecutar las otras bifurcaciones.Si <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> no se evalúa como **true**, la actividad <xref:System.Activities.Statements.ParallelForEach%601> se completa una vez se hayan completado todas sus actividades secundarias.  
  
## Actividad ParallelForEach\<T\>  
 <xref:System.Activities.Statements.ParallelForEach%601> enumera sus valores y programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera.Solo programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.La forma en que efectúe el cuerpo la ejecución depende de si <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pasa a estado inactivo.  
  
 Si la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> no pasa a estado inactivo, se ejecuta en orden inverso porque las actividades programadas se administran como una pila, la última actividad programada se ejecuta primero.Por ejemplo, si tiene una colección de {1,2,3,4} en <xref:System.Activities.Statements.ParallelForEach%601> y utiliza **WriteLine** como cuerpo para escribir el valor,en la consola, tendrá impreso 4, 3, 2, 1.Esto se debe a que **WriteLine** no pasa a estado inactivo, por ello tras la programar 4 actividades **WriteLine**, estas se ejecutan comportándose como una pila \(la primera en entrar es la última en salir\).  
  
 Pero si tiene actividades en la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pueden pasar a estado inactivo, como una actividad <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>,A continuación no hay necesidad de esperarlos para completarse.<xref:System.Activities.Statements.ParallelForEach%601> va a la siguiente actividad de cuerpo programada e intenta ejecutarla.Si esa actividad también pasa a estado inactivo, <xref:System.Activities.Statements.ParallelForEach%601> vuelve a desplazarse hasta la siguiente actividad del cuerpo.  
  
### Utilizar el diseñador de actividades ParallelForEach\<T\>  
 El diseñador de actividades **ParallelForEach\<T\>** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **ParallelForEach\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente los diseñadores de actividades, por ejemplo, en un diseñador de actividades **Sequence**.Después de colocarlo en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], crea una actividad <xref:System.Activities.Statements.ParallelForEach%601>, que de forma predeterminada contiene una propiedad <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach\<Int32\>.**  
  
### Propiedades ParallelForEach\<T\> en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ParallelForEach%601> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado.El valor predeterminado es **ParallelForEach\<Int32\>**.De forma opcional, el valor se puede editar en la cuadrícula **Propiedades** o directamente en el encabezado del diseñador de actividades.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|La actividad que se va a ejecutar para cada elemento en la colección.Para agregar la actividad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, coloque una actividad del cuadro de herramientas en el cuadro **Body** del diseñador de actividades **ParallelForEach\<T\>** donde aparezca el texto con la sugerencia "Coloque la actividad aquí".|  
|**TypeArgument**|True|El tipo de elementos en la colección de <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> especificada por el parámetro genérico *T*.De manera predeterminada, **TypeArgument** se establece en **Int32**.Para cambiar el tipo T en el diseñador de actividades **ParallelForEach\<T\>**, cambie el valor del cuadro combinado **TypeArgument** en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|La colección de elementos por la que se realizará la iteración.Para establecer la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, escriba una expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en el cuadro **Valores** del diseñador de actividad **ForEach\<T\>** en el cuadro con el texto de la sugerencia "Escriba una expresión de VB" o en el cuadro **Valores** de la ventana **Propiedades**.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Se evalúa cuando se completa cada iteración.Si se evalúa como true, se cancelan las operaciones programadas pendientes.Si no se establece esta propiedad, se ejecutan todas las instrucciones programadas hasta su compleción.|  
  
 De forma predeterminada, el iterador del bucle se denomina elemento.Puede cambiar el nombre de la variable de iterador en el cuadro **ForEach** del diseñador de actividad **ParallelForEach\<T\>**.El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ParallelForEach%601>.  
  
## Vea también  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)