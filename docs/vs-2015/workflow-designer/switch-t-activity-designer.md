---
title: Conmutador&lt;T&gt; Diseñador de actividad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e2baacdfb35e2360a0e9dcc56891cadbe7d3ff3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997628"
---
# <a name="switchlttgt-activity-designer"></a>Conmutador&lt;T&gt; Diseñador de actividad
La actividad <xref:System.Activities.Statements.Switch%601> evalúa una expresión especificada y ejecuta la actividad desde una colección de actividades cuya clave asociada se corresponde con el valor que se ha obtenido a partir de la evaluación.  
  
 El **conmutador\<T >** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.Switch%601> actividad en el [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="the-switchtactivity"></a>El modificador\<T > actividad  
 Una actividad <xref:System.Activities.Statements.Switch%601> contiene una propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y un diccionario de propiedades <xref:System.Activities.Statements.Switch%601.Cases%2A>. Cada caso en el diccionario consta de un par que contiene un *clave* y una actividad que actúa como el correspondiente *valor*. La actividad <xref:System.Activities.Statements.Switch%601> evalúa la propiedad <xref:System.Activities.Statements.Switch%601.Expression%2A> y la compara con cada una de las claves. Si se encuentra una coincidencia, se ejecuta la actividad correspondiente. Solo es posible que se dé una coincidencia porque las claves del diccionario deben ser únicas de acuerdo al tipo de igualdad que ha definido el comparador de igualdad del diccionario. Si no se encuentran coincidencias, se ejecuta la actividad <xref:System.Activities.Statements.Switch%601.Default%2A>.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Cómo utilizar el modificador\<T > Diseñador de actividad  
 El **conmutador\<T >** Diseñador de actividad puede encontrarse en el **flujo de Control** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **Cuadro de herramientas** ficha la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.) Después de colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)], muestra la **seleccionar tipos** cuadro de diálogo para permitir al usuario especificar el tipo genérico *T* utilizados en <xref:System.Activities.Statements.Switch%601> actividad. El valor predeterminado es **Int32**. Una vez que el tipo genérico *T* se ha seleccionado un **conmutador\<T >** diseñador se agrega en el Diseñador de flujo de trabajo.  
  
 Éstas son las propiedades de **conmutador\<T >** diseñador. La totalidad de estas propiedades se pueden editar en cuadrícula de propiedades. Algunas de ellas también se pueden editar en la superficie del diseñador.  
  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.Switch%601> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Switch%601>. El valor predeterminado es Switch\<Int32 >. El valor puede modificarse en el **propiedades** ventana o directamente en el encabezado del diseñador.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Especifica la expresión que se utiliza para comparar con las claves en la colección de casos con el fin de determinar el caso que se va a ejecutar.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica la actividad que se va a ejecutar si no se encuentran coincidencias. Haga clic en el **agregar una actividad** botón en el diseñador para abrir el **predeterminado** cuadro donde se puede colocar la actividad.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica los casos que se van a evaluar. Para agregar un caso, haga clic en el **Agregar nuevo caso** situado en la parte inferior de **conmutador\<T >** diseñador. El botón cambia a un cuadro de texto (cuadro combinado si el tipo genérico se seleccionó al agregar el modificador\<T > es String o Enum). Después de agregar una clave en el **valor de Case** cuadro, el área de caso se expande y se puede colocar una actividad donde el texto de la sugerencia "Coloque la actividad aquí" para definir la lógica de ejecución para el caso.|  
  
 Se pueden agregar varios casos con tal de que no se dupliquen las claves de caso. De lo contrario, aparece un cuadro de diálogo de error donde se indica que ya existe la clave de caso y que debe elegir una diferente. En el **conmutador\<T >** diseñador, puede ser solo un área de caso en la vista ampliada a la vez. Si un área de caso está en vista contraída, se expandirá al hacer clic en el área de caso. Observe que para un caso contraído, el diseñador muestra el nombre para mostrar de la actividad dentro del caso en la parte derecha, en su caso. Si no, se muestra el **agregar una actividad** botón que se expande el caso si hace clic en él y le permite agregar una actividad.  
  
 Al hacer clic en la clave de caso existente, cambia la clave de etiqueta a cuadro de texto de forma que pueda editar la clave de caso.  
  
 Existen dos maneras de eliminar un caso:  
  
1. Seleccione el caso y elimínelo.  
  
2. Seleccione el caso, contextual para mostrar el menú contextual y seleccione **eliminar**.  
  
   Observe que es preciso seleccionar el propio caso para eliminarlo. Cuando se selecciona y elimina la actividad dentro de un caso solo se elimina la actividad y no el caso.  
  
## <a name="see-also"></a>Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)