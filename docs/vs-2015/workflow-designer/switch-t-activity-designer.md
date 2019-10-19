---
title: Cambiar &lt;T &gt; diseñador de actividad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb6d4eb189b75d6e401bca0cfe50a71081760478
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660098"
---
# <a name="switchlttgt-activity-designer"></a>Cambiar &lt;T diseñador de actividad &gt;
La actividad <xref:System.Activities.Statements.Switch%601> evalúa una expresión especificada y ejecuta la actividad desde una colección de actividades cuya clave asociada se corresponde con el valor que se ha obtenido a partir de la evaluación.

 El diseñador de **\<T >** diseñador de actividad se usa para crear y configurar una actividad de <xref:System.Activities.Statements.Switch%601> en el [!INCLUDE[wfd1](../includes/wfd1-md.md)].

## <a name="the-switchtactivity"></a>El modificador \<T actividad >
 Una actividad <xref:System.Activities.Statements.Switch%601> contiene una propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y un diccionario de propiedades <xref:System.Activities.Statements.Switch%601.Cases%2A>. Cada caso del diccionario está formado por un par que contiene una *clave* y una actividad que actúa como su *valor*correspondiente. La actividad <xref:System.Activities.Statements.Switch%601> evalúa la propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y la compara con cada una de las claves. Si se encuentra una coincidencia, se ejecuta la actividad correspondiente. Solo es posible que se dé una coincidencia porque las claves del diccionario deben ser únicas de acuerdo al tipo de igualdad que ha definido el comparador de igualdad del diccionario. Si no se encuentran coincidencias, se ejecuta la actividad <xref:System.Activities.Statements.Switch%601.Default%2A>.

## <a name="how-to-use-the-switcht-activity-designer"></a>Cómo usar el diseñador de actividad switch \<T >
 El diseñador de actividades de **\<T >** se puede encontrar en la categoría **flujo de control** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en la **vista.** o Ctrl + Alt + X). Después de colocarlo en el [!INCLUDE[wfd2](../includes/wfd2-md.md)], se muestra el cuadro de diálogo **seleccionar tipos** para permitir que el usuario especifique el tipo genérico *t* usado en 1 actividad. El valor predeterminado es **Int32**. Una vez que se ha seleccionado el tipo genérico *T* , se agrega un **modificador \<T** diseñador de > al diseñador de flujo de trabajo.

 A continuación se muestran las propiedades de **Switch \<T >** Designer. La totalidad de estas propiedades se pueden editar en cuadrícula de propiedades. Algunas de ellas también se pueden editar en la superficie del diseñador.

 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Switch%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Switch%601>. El valor predeterminado es switch \<Int32 >. El valor se puede editar en la ventana **propiedades** o directamente en el encabezado del diseñador.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Especifica la expresión que se utiliza para comparar con las claves en la colección de casos con el fin de determinar el caso que se va a ejecutar.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica la actividad que se va a ejecutar si no se encuentran coincidencias. Haga clic en el botón **Agregar una actividad** en el diseñador para abrir el cuadro **predeterminado** donde se puede quitar la actividad.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica los casos que se van a evaluar. Para agregar un caso, haga clic en el botón **Agregar nuevo caso** situado en la parte inferior de **cambiar \<T** diseñador de >. El botón cambia a un cuadro de texto (cuadro combinado si el tipo genérico seleccionado al agregar el modificador \<T > es una cadena o una enumeración). Después de agregar una clave en el cuadro **valor de caso** , el área de caso se expande y se puede quitar una actividad donde el texto de la sugerencia "Coloque la actividad aquí" para definir la lógica de ejecución para el caso.|

 Se pueden agregar varios casos con tal de que no se dupliquen las claves de caso. De lo contrario, aparece un cuadro de diálogo de error donde se indica que ya existe la clave de caso y que debe elegir una diferente. En el diseñador de **> de \<T modificador** , solo un área de caso puede estar en la vista expandida a la vez. Si un área de caso está en vista contraída, se expandirá al hacer clic en el área de caso. Observe que para un caso contraído, el diseñador muestra el nombre para mostrar de la actividad dentro del caso en la parte derecha, en su caso. De lo contrario, muestra el botón **Agregar una actividad** que amplía el caso si hace clic en él y le permite agregar una actividad.

 Al hacer clic en la clave de caso existente, cambia la clave de etiqueta a cuadro de texto de forma que pueda editar la clave de caso.

 Existen dos maneras de eliminar un caso:

1. Seleccione el caso y elimínelo.

2. Seleccione el caso, haga clic con el botón derecho para mostrar el menú contextual y seleccione **eliminar**.

   Observe que es preciso seleccionar el propio caso para eliminarlo. Cuando se selecciona y elimina la actividad dentro de un caso solo se elimina la actividad y no el caso.

## <a name="see-also"></a>Vea también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)