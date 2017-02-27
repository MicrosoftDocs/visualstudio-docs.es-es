---
title: "Dise&#241;ador de actividades Switch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Dise&#241;ador de actividades Switch&lt;T&gt;
La actividad <xref:System.Activities.Statements.Switch%601> evalúa una expresión especificada y ejecuta la actividad desde una colección de actividades cuya clave asociada se corresponde con el valor que se ha obtenido a partir de la evaluación.  
  
 El diseñador de actividades **Switch\<T\>** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Switch%601> en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## Actividad Switch\<T\>  
 Una actividad <xref:System.Activities.Statements.Switch%601> contiene una propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y un diccionario de propiedades <xref:System.Activities.Statements.Switch%601.Cases%2A>.Cada caso en el diccionario está compuesto por una pareja que contiene una *key* y una actividad que actúa como su *value* correspondiente.La actividad <xref:System.Activities.Statements.Switch%601> evalúa la propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y la compara con cada una de las claves.Si se encuentra una coincidencia, se ejecuta la actividad correspondiente.Solo es posible que se dé una coincidencia porque las claves del diccionario deben ser únicas de acuerdo al tipo de igualdad que ha definido el comparador de igualdad del diccionario.Si no se encuentran coincidencias, se ejecuta la actividad <xref:System.Activities.Statements.Switch%601.Default%2A>.  
  
## Utilizar el diseñador de actividades Switch\<T\>  
 El diseñador de actividades **Switch\<T\>** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\). Después de colocarlo en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], muestra el cuadro de diálogo **Seleccionar tipos** para que el usuario pueda especificar el tipo genérico *T* que se utiliza en la actividad <xref:System.Activities.Statements.Switch%601>.El valor predeterminado es **Int32**.Una vez se ha seleccionado el tipo genérico *T*, se agrega un diseñador **Switch\<T\>** al diseñador de flujo de trabajo.  
  
 A continuación, se especifican las propiedades del diseñador **Switch\<T\>**.La totalidad de estas propiedades se pueden editar en cuadrícula de propiedades.Algunas de ellas también se pueden editar en la superficie del diseñador.  
  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Switch%601> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Switch%601>.El valor predeterminado es Switch\<Int32\>.El valor se puede editar en la ventana **Propiedades** o directamente en el encabezado de diseñador.<br /><br /> Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Especifica la expresión que se utiliza para comparar con las claves en la colección de casos con el fin de determinar el caso que se va a ejecutar.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica la actividad que se va a ejecutar si no se encuentran coincidencias.Haga clic en el botón **Agregar una actividad** en el diseñador para abrir el cuadro **Predeterminado** donde se puede colocar la actividad.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica los casos que se van a evaluar.Para agregar un caso, haga clic en el botón **Agregar nuevo caso** en la parte inferior del diseñador **Switch\<T\>**.El botón cambia a un cuadro de texto \(un cuadro combinado si el tipo genérico que se seleccionó al agregar Switch\<T\> es String o Enum\).Después de agregar una clave en el cuadro **Valor de caso**, el área del caso se expande y se puede colocar una actividad donde aparece el texto "Coloque la actividad aquí" para definir la lógica de ejecución que corresponde al caso.|  
  
 Se pueden agregar varios casos con tal de que no se dupliquen las claves de caso.De lo contrario, aparece un cuadro de diálogo de error donde se indica que ya existe la clave de caso y que debe elegir una diferente.En el diseñador **Switch\<T\>**, solo una área de caso puede tener la vista expandida de cada vez.Si una área de caso está en vista contraída, se expandirá al hacer clic en el área de caso.Observe que para un caso contraído, el diseñador muestra el nombre para mostrar de la actividad dentro del caso en la parte derecha, en su caso.De lo contrario, muestra el botón **Agregar una actividad** que expande el caso al hacer clic en él y le permite agregar una actividad.  
  
 Al hacer clic en la clave de caso existente, cambia la clave de etiqueta a cuadro de texto de forma que pueda editar la clave de caso.  
  
 Existen dos maneras de eliminar un caso:  
  
1.  Seleccione el caso y elimínelo.  
  
2.  Seleccione el caso, haga clic con el botón secundario del mouse para que aparezca el menú contextual y seleccione **Eliminar**.  
  
 Observe que es preciso seleccionar el propio caso para eliminarlo.Cuando se selecciona y elimina la actividad dentro de un caso solo se elimina la actividad y no el caso.  
  
## Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)