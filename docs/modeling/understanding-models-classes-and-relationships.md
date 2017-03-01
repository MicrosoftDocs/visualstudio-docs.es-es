---
title: "Descripción de los modelos, las clases y relaciones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 35
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 4982dcc5c6fb0184f1f467971b6255aace6bec53
ms.lasthandoff: 02/22/2017

---
# <a name="understanding-models-classes-and-relationships"></a>Introducción a los modelos, las clases y las relaciones
Un lenguaje específico de dominio (DSL) se define por su archivo de definición de DSL, junto con cualquier código de programa personalizado que se haya escrito. La mayoría del código de programa en la solución de DSL se genera a partir de este archivo.  
  
 Este tema explica las características principales de la definición de DSL.  
  
## <a name="the-dsl-definition"></a>La definición de DSL  
 Cuando se abre `Dsl\DslDefinition.dsl`, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ventana similar a la siguiente imagen.  
  
 ![Diseñador DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 La información más importante en la definición de DSL se muestra en el diagrama de la definición de DSL. Obtener información adicional, que también forma parte de DslDefinition.dsl, se muestra en el Explorador de DSL, que normalmente aparece en la parte del diagrama. Trabajar con el diagrama para las tareas más frecuentes y con el Explorador de DSL de personalizaciones más avanzadas.  
  
 El diagrama de la definición de DSL muestra las clases de dominio que definen los elementos del modelo y las relaciones que definen vínculos entre elementos del modelo. También muestra las formas y conectores que se usan para mostrar los elementos del modelo para el usuario.  
  
 ![Diseñador DSL con swimlane](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Cuando se selecciona un elemento en la definición de DSL, en el diagrama o en el Explorador de DSL, se muestra información sobre él en la ventana Propiedades. Información adicional puede mostrarse en la ventana Detalles de DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Los modelos son instancias de DSL  
 Un *modelo* es una instancia de su DSL creada por un usuario. Un modelo contiene elementos del modelo, que son instancias de las clases de dominio que defina y vínculos entre los elementos, que son instancias de las relaciones de dominio que defina. También puede tener un modelo de formas y conectores, que muestra los elementos del modelo y los vínculos en un diagrama. La definición de DSL incluye las clases de forma, conector clases y una clase para el diagrama.  
  
 Una definición de DSL también es conocido como un *modelo de dominio*. Un modelo de dominio o la definición de DSL es la representación en tiempo de diseño del lenguaje específico de dominio, mientras que el modelo es la creación de instancias de tiempo de ejecución del lenguaje específico de dominio.  
  
## <a name="domain-classes-define-model-elements"></a>Clases de dominio definen elementos de modelo  
 Clases de dominio se utilizan para crear los diversos elementos en el dominio y las relaciones de dominio son los vínculos entre los elementos. Son la representación en tiempo de diseño de los elementos y vínculos que se crearán instancias por los usuarios del lenguaje de diseño específicas cuando crean sus modelos.  
  
 Esta ilustración muestra un modelo que se ha creado por el usuario de una biblioteca de música DSL. Álbumes de música se representan mediante cuadros que contienen listas de canciones. Artistas se representan mediante cuadros de esquinas redondeadas y están conectados a los álbumes que han contribuido.  
  
 ![Modelo de instancia de DSL generado](../modeling/media/music_instance.png "Music_Instance")  
  
 La definición de DSL separa dos aspectos. La apariencia de los elementos del modelo en el diagrama del modelo se define mediante las clases de forma y las clases de conector. La información incluida en el modelo se define mediante clases de dominio y las relaciones de dominio.  
  
 La ilustración siguiente muestra las clases de dominio y las relaciones en la definición de DSL de la biblioteca de música.  
  
 ![Relaciones de incrustación y referencia](../modeling/media/music_classes.png "Music_Classes")  
  
 La ilustración muestra cuatro clases de dominio: música, álbum, intérprete y canción. Las clases de dominio definen propiedades de dominio como nombre, título y así sucesivamente. En el modelo de instancia, los valores de algunas de estas propiedades se muestran en el diagrama.  
  
 Entre las clases son las relaciones de dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs y ArtistAppearedOnAlbums. Las relaciones tienen multiplicidades como 1..1, 0.. *. Por ejemplo, todas las canciones deben estar relacionado con exactamente un álbum a través de la relación AlbumHasSongs. Cada álbum puede tener cualquier número de canciones.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Reorganizar el diagrama de la definición de DSL  
 Observe que una clase de dominio puede aparecer varias veces en el diagrama de la definición de DSL, como álbum en esta imagen. Siempre hay una vista principal y puede haber algunos *referencia* vistas.  
  
 Para reorganizar el diagrama de la definición de DSL, puede:  
  
-   Intercambiar principal y hacer referencia a vistas utilizando la **Traer árbol aquí** y **división árbol** comandos. Haga clic en una clase de dominio individual para ver estos comandos.  
  
-   Cambiar el orden de las clases de dominio y las clases de formas, presione Ctrl+flecha arriba y Ctrl+flecha abajo.  
  
-   Contraer o expandir mediante el icono en la superior derecha de cada forma de clases.  
  
-   Contraer partes del árbol haciendo clic en el signo menos (-) en la parte inferior de una clase de dominio.  
  
## <a name="inheritance"></a>Herencia  
 Clases de dominio pueden definirse mediante herencia. Para crear una derivación de herencia, haga clic en la herramienta de herencia, haga clic en la clase derivada y, a continuación, haga clic en la clase base. Un elemento de modelo tiene todas las propiedades que se definen en su propia clase de dominio, junto con todas las propiedades heredadas de la clase base. También hereda sus roles en las relaciones.  
  
 También puede utilizarse la herencia entre relaciones, formas y conectores. Deje la herencia dentro del mismo grupo. Una forma no puede heredar de una clase de dominio.  
  
## <a name="domain-relationships"></a>Relaciones de dominio  
 Las relaciones se pueden vincular elementos de modelo. Vínculos siempre son binarios; vinculan exactamente dos elementos. Sin embargo, cualquier elemento puede tener muchos vínculos a otros objetos e incluso puede haber más de un vínculo entre el mismo par de elementos.  
  
 Igual que se pueden definir clases diferentes de elementos, puede definir diferentes clases de vínculos. Se llama a la clase de un vínculo de un *relación de dominio*. Una relación de dominio especifica qué clases de elemento se pueden conectar sus instancias. Cada extremo de una relación se denomina un *rol*, y la relación de dominio define los nombres de las dos funciones, así como para la propia relación.  
  
 Hay dos tipos de relaciones de dominio: incrustar relaciones y referencia. En el diagrama de la definición de DSL, relaciones de incrustación tienen líneas sólidas en cada rol y las relaciones de referencia hayan líneas de guiones.  
  
### <a name="embedding-relationships"></a>Relaciones de incrustación  
 Cada elemento de un modelo, salvo por su raíz es el destino de un vínculo de incrustación. Por lo tanto, todo el modelo conforma un único árbol de incrustación de vínculos. Una relación de incrustación representa contención o la propiedad. Dos elementos de modelo que están relacionados de esta manera son también conocido como primarios y secundarios. El elemento secundario se dice que se incrustan en el elemento primario.  
  
 Vínculos de incrustación no normalmente aparecen explícitamente como conectores en un diagrama. En su lugar, normalmente se representan mediante la contención. El diagrama representa la raíz del modelo y elementos incrustados en ella se muestran como formas del diagrama.  
  
 En el ejemplo, la clase raíz música tiene una relación de incrustación MusicHasAlbums al álbum, que tiene un AlbumHasSongs incrustación canción. Canciones se muestran como elementos en una lista dentro de cada álbum. Música también tiene una incrustación MusicHasArtists a la clase artista, cuyas instancias también aparecen como formas en el diagrama.  
  
 De forma predeterminada, los elementos incrustados se eliminan automáticamente cuando se eliminan sus elementos primarios.  
  
 Cuando se guarda un modelo de archivos en formato XML, los elementos incrustados están anidados dentro de sus elementos primarios, a menos que haya personalizado la serialización.  
  
> [!NOTE]
>  Incrustación no es lo mismo que herencia. Elementos secundarios en una relación de incrustación no heredan las propiedades del elemento primario. Una incrustación es un tipo de vínculo entre los elementos del modelo. Herencia es una relación entre clases y no crea vínculos entre elementos del modelo.  
  
### <a name="embedding-rules"></a>Reglas de incrustación  
 Cada elemento de un modelo de instancia debe ser el destino de exactamente un vínculo de incrustación, excepto la raíz del modelo.  
  
 Por lo tanto, cada clase de dominio no abstracta, excepto la clase raíz, debe ser el destino de al menos una relación de incrustación o deben heredar una incrustación de una clase base. Una clase puede ser el destino de incrustaciones de dos o más, pero sus elementos de modelo de instancia sólo pueden tener un elemento primario a la vez. La multiplicidad del destino al origen debe ser de 0.. 1 o 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>El explorador muestra el árbol de incrustación  
 La definición de DSL crea también un explorador, que los usuarios ven junto con su diagrama de modelo.  
  
 ![Explorador generado de DSL](../modeling/media/music_explorer.png "Music_Explorer")  
  
 El explorador muestra todos los elementos en el modelo, incluso aquellos para los que no ha definido ninguna forma. Muestra los elementos y relaciones de incrustación, pero no hacer referencia a las relaciones.  
  
 Para ver los valores de las propiedades de dominio de un elemento, el usuario selecciona un elemento en el diagrama del modelo o en el Explorador de modelos y abre la ventana Propiedades. Muestra todas las propiedades de dominio, los que no se muestran en el diagrama incluidos. En el ejemplo, cada canción tiene un título y género, pero solo el valor de título se muestra en el diagrama.  
  
## <a name="reference-relationships"></a>Relaciones de referencia  
 Una relación de referencia representa cualquier tipo de relación que no es incrustar.  
  
 Relaciones de referencia normalmente se muestran en un diagrama como conectores entre las formas.  
  
 En la representación XML del modelo, un vínculo de referencia entre dos elementos se representa mediante *monikers.* Es decir, monikers son nombres que identifican de forma única cada elemento en el modelo. El nodo XML para cada elemento del modelo contiene un nodo que especifica el nombre de la relación y el moniker del otro elemento.  
  
## <a name="roles"></a>Roles  
 Cada relación de dominio tiene dos funciones, una función de origen y un rol de destino.  
  
 En la siguiente imagen, la línea entre el **Publisher** clase de dominio y el **PublisherCatalog** relación de dominio es el rol de origen. La línea entre la relación de dominio y el **álbum** clase de dominio es la función de destino.  
  
 ![Las funciones y propiedades. ] (../modeling/media/propertycode.png "PropertyCode")  
  
 Los nombres asociados con una relación son especialmente importantes cuando se escribe código de programa que atraviesa el modelo. Por ejemplo, al compilar la solución de DSL, el publicador de la clase generada tiene una propiedad de catálogo que es un conjunto de álbumes. La clase álbum tiene una publicador que es una instancia única de la clase de Editor de propiedad.  
  
 Al crear una relación en una definición de DSL, los nombres de propiedad y relación tienen valores predeterminados. Sin embargo, puede cambiarlos.  
  
## <a name="multiplicities"></a>Multiplicidades  
 Multiplicidades especifican cuántos elementos tienen la misma función en una relación de dominio. En el ejemplo, el cero a varios (0..\*) configuración de multiplicidad en el **catálogo** rol especifica que cualquier instancia de la **Publisher** clase de dominio puede tener tantos **PublisherCatalog** vínculos de relación que desee darle.  
  
 Configurar la multiplicidad de un rol escribiendo en el diagrama o modificando la `Multiplicity` propiedad en el **propiedades** ventana. En la tabla siguiente describe la configuración de esta propiedad.  
  
|Tipo de multiplicidad|Descripción|  
|-----------------------|-----------------|  
|0.. * (cero a varios)|Cada instancia de la clase de dominio puede tener varias instancias de la relación o ninguna instancia de la relación.|  
|De&0; a&1; (cero a uno)|Cada instancia de la clase de dominio puede tener no más de una instancia de la relación o ninguna instancia de la relación.|  
|1..1 (uno)|Cada instancia de la clase de dominio puede tener una instancia de la relación. No se puede crear más de una instancia de esta relación desde cualquier instancia de la clase de función. Si está habilitada la validación, aparecerá un error de validación cuando cualquier instancia de la clase de función no tiene ninguna instancia de la relación.|  
|1.. * (uno a varios)|Cada instancia de la clase en el rol que tiene este multiplicidad puede tener varias instancias de la relación y cada instancia debe tener al menos una instancia de la relación. Si está habilitada la validación, aparecerá un error de validación cuando cualquier instancia de la clase de función no tiene ninguna instancia de la relación.|  
  
## <a name="domain-relationships-as-classes"></a>Relaciones de dominio como clases  
 Un vínculo se representa en el almacén como una instancia de LinkElement, que es una clase derivada de ModelElement. Puede definir estas propiedades en el diagrama de modelo de dominio en las relaciones de dominio.  
  
 También puede hacer una relación de origen o destino de otras relaciones. En el diagrama de modelo de dominio, haga clic en la relación de dominio y, a continuación, haga clic en **mostrar como clase**. Aparecerá un cuadro de clase adicional. Relaciones, a continuación, puede conectarse a él.  
  
 Puede definir una relación parcialmente por herencia, igual que con las clases de dominio. Seleccione la relación derivada y establezca **relación Base** en la ventana Propiedades.  
  
 Una relación derivada especializa su relación de base. El dominio de las clases que TI vínculos se deben derivar de o igual que las clases vinculadas mediante la relación base. Cuando se crea un vínculo de la relación derivada de un modelo, es una instancia de la derivada y las relaciones bases. En el código de programa, puede navegar con el extremo opuesto del vínculo mediante las propiedades generadas por la base o la clase derivada.  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

