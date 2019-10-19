---
title: Descripción de los modelos, las clases y las relaciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5426c6f8e9c4a932430a0c3bd3df6d98400c3562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659557"
---
# <a name="understanding-models-classes-and-relationships"></a>Introducción a los modelos, las clases y las relaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un lenguaje específico de dominio (DSL) se define mediante su archivo de definición de DSL, junto con cualquier código de programa personalizado que pueda escribir. La mayor parte del código de programa de la solución DSL se genera a partir de este archivo.

 En este tema se explican las características centrales de la definición de DSL.

## <a name="the-dsl-definition"></a>La definición de DSL
 Al abrir `Dsl\DslDefinition.dsl`, la ventana de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se parece a la siguiente imagen.

 ![diseñador DSL](../modeling/media/dsl-designer.png "dsl_designer")

 La información más importante en la definición de DSL se muestra en el diagrama de definición de DSL. La información adicional, que también forma parte de DslDefinition. DSL, se muestra en el explorador de DSL, que normalmente aparece en el lateral del diagrama. Trabajará con el diagrama de las tareas más frecuentes y con DSL Explorer para realizar personalizaciones más avanzadas.

 En el diagrama de definición de DSL se muestran las clases de dominio que definen los elementos del modelo y las relaciones que definen los vínculos entre los elementos del modelo. También se muestran las formas y los conectores que se usan para mostrar los elementos del modelo al usuario.

 ![diseñador DSL con calle](../modeling/media/dsl-desinger.png "dsl_desinger")

 Al seleccionar un elemento de la definición de DSL, en el diagrama o en el explorador de DSL, se muestra información sobre él en el ventana Propiedades. Es posible que se muestre información adicional en la ventana detalles de DSL.

### <a name="models-are-instances-of-dsls"></a>Los modelos son instancias de DSL
 Un *modelo* es una instancia de su DSL creada por un usuario. Un modelo contiene elementos del modelo, que son instancias de las clases de dominio que define, y vínculos entre los elementos, que son instancias de las relaciones de dominio que defina. Un modelo también puede tener formas y conectores, que muestran los elementos del modelo y los vínculos de un diagrama. La definición de DSL incluye las clases de forma, las clases de conector y una clase para el diagrama.

 Una definición de DSL también se conoce como *modelo de dominio*. Una definición de DSL o un modelo de dominio es la representación en tiempo de diseño del lenguaje específico del dominio, mientras que el modelo es la creación de instancias en tiempo de ejecución del lenguaje específico del dominio.

## <a name="domain-classes-define-model-elements"></a>Clases de dominio definir elementos de modelo
 Las clases de dominio se usan para crear los distintos elementos del dominio y las relaciones de dominio son los vínculos entre los elementos. Son la representación en tiempo de diseño de los elementos y vínculos de los que se crearán instancias de los usuarios del lenguaje específico del diseño cuando creen sus modelos.

 En esta ilustración se muestra un modelo creado por el usuario de un DSL de biblioteca de música. Los álbumes de música se representan mediante cuadros que contienen listas de canciones. Los artistas se representan mediante cuadros con esquinas redondeadas y se conectan a los álbumes en los que han contribuido.

 ![Modelo de instancia de DSL generado](../modeling/media/music-instance.png "Music_Instance")

 La definición de DSL separa dos aspectos. La apariencia de los elementos del modelo en el diagrama del modelo se define mediante clases de forma y clases de conector. La información que se lleva a cabo en el modelo se define mediante clases de dominio y relaciones de dominio.

 En la ilustración siguiente se muestran las clases de dominio y las relaciones de la definición de DSL de la biblioteca de música.

 ![Incrustación y relaciones de referencia](../modeling/media/music-classes.png "Music_Classes")

 En la ilustración se muestran cuatro clases de dominio: música, álbum, artista y canción. Las clases de dominio definen propiedades de dominio como name, title, etc. En el modelo de instancia, los valores de algunas de estas propiedades se muestran en el diagrama.

 Entre las clases están las relaciones de dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs y ArtistAppearedOnAlbums. Las relaciones tienen multiplicidades como 1.. 1, 0.. *. Por ejemplo, cada canción debe estar relacionada con exactamente un álbum a través de la relación AlbumHasSongs. Cada álbum puede tener cualquier número de canciones.

### <a name="rearranging-the-dsl-definition-diagram"></a>Reorganizar el diagrama de definición de DSL
 Tenga en cuenta que una clase de dominio puede aparecer varias veces en el diagrama de definición de DSL, como álbum en esta imagen. Siempre hay una vista principal y puede haber algunas vistas de *referencia* .

 Para reorganizar el diagrama de definición de DSL, puede:

- Intercambie vistas principales y de referencia mediante los comandos **traer árbol aquí** y **dividir árbol** . Haga clic con el botón secundario en una sola clase de dominio para ver estos comandos.

- Vuelva a ordenar las clases de dominio y las clases de formas presionando Ctrl + flecha arriba y Ctrl + flecha abajo.

- Contraer o expandir clases con el icono situado en la parte superior derecha de cada forma.

- Para contraer partes del árbol, haga clic en el signo menos (-) situado en la parte inferior de una clase de dominio.

## <a name="inheritance"></a>Herencia
 Las clases de dominio se pueden definir mediante la herencia. Para crear una derivación de herencia, haga clic en la herramienta herencia, haga clic en la clase derivada y, a continuación, haga clic en la clase base. Un elemento de modelo tiene todas las propiedades que se definen en su propia clase de dominio, junto con todas las propiedades heredadas de la clase base. También hereda sus roles en las relaciones.

 La herencia también puede usarse entre relaciones, formas y conectores. La herencia debe mantenerse dentro del mismo grupo. Una forma no puede heredar de una clase de dominio.

## <a name="domain-relationships"></a>Relaciones de dominio
 Los elementos de modelo se pueden vincular mediante relaciones. Los vínculos siempre son binarios; vinculan exactamente dos elementos. Sin embargo, cualquier elemento puede tener muchos vínculos a otros objetos y incluso puede haber más de un vínculo entre el mismo par de elementos.

 Del mismo modo que puede definir diferentes clases de elementos, puede definir diferentes clases de vínculos. La clase de un vínculo se denomina *relación de dominio*. Una relación de dominio especifica las clases de elemento a las que se pueden conectar sus instancias. Cada extremo de una relación se denomina *rol*y la relación de dominio define los nombres de los dos roles, así como la propia relación.

 Hay dos tipos de relaciones de dominio: incrustar relaciones y relaciones de referencia. En el diagrama de definición de DSL, las relaciones de incrustación tienen líneas sólidas en cada rol y las relaciones de referencia tienen líneas discontinuas.

### <a name="embedding-relationships"></a>Incrustar relaciones
 Todos los elementos de un modelo, excepto su raíz, son el destino de un vínculo de incrustación. Por lo tanto, todo el modelo forma un único árbol de vínculos de incrustación. Una relación de incrustación representa la contención o la propiedad. Dos elementos de modelo que se relacionan de esta manera también se conocen como primario y secundario. Se dice que el elemento secundario está incrustado en el elemento primario.

 Los vínculos de incrustación no se suelen mostrar explícitamente como conectores en un diagrama. En su lugar, normalmente se representan mediante contención. La raíz del modelo se representa mediante el diagrama y los elementos incrustados en ella se muestran como formas en el diagrama.

 En el ejemplo, la clase raíz Music tiene una relación de incrustación MusicHasAlbums a album, que tiene una incrustación AlbumHasSongs en Song. Las canciones se muestran como elementos en una lista dentro de cada álbum. La música también tiene un MusicHasArtists de inserción para la clase artista, cuyas instancias también aparecen como formas en el diagrama.

 De forma predeterminada, los elementos incrustados se eliminan automáticamente cuando se eliminan sus elementos primarios.

 Cuando se guarda un modelo en un archivo en formato XML, los elementos incrustados se anidan dentro de sus elementos primarios, a menos que haya personalizado la serialización.

> [!NOTE]
> Incrustación no es lo mismo que herencia. Los elementos secundarios de una relación de incrustación no heredan las propiedades del elemento primario. Una inserción es un tipo de vínculo entre los elementos del modelo. La herencia es una relación entre las clases y no crea vínculos entre los elementos del modelo.

### <a name="embedding-rules"></a>Incrustar reglas
 Cada elemento de un modelo de instancia debe ser el destino de exactamente un vínculo de incrustación, excepto la raíz del modelo.

 Por lo tanto, todas las clases de dominio no abstractas, excepto la clase raíz, deben ser el destino de al menos una relación de incrustación, o debe heredar una inserción de una clase base. Una clase puede ser el destino de dos o más incrustaciones, pero sus elementos de modelo de instancia solo pueden tener un elemento primario a la vez. La multiplicidad del destino al origen debe ser 0.. 1 o 1.. 1.

### <a name="the-explorer-displays-the-embedding-tree"></a>El explorador muestra el árbol de incrustación
 La definición de DSL también crea un explorador, que los usuarios ven junto con el diagrama del modelo.

 ![Explorador generado de DSL](../modeling/media/music-explorer.png "Music_Explorer")

 En el explorador se muestran todos los elementos del modelo, incluso aquellos para los que no se han definido formas. Muestra los elementos y las relaciones de incrustación, pero no las relaciones de referencia.

 Para ver los valores de las propiedades de dominio de un elemento, el usuario selecciona un elemento, ya sea en el diagrama del modelo o en el explorador de modelos, y abre el ventana Propiedades. Muestra todas las propiedades de dominio, incluidas las que no se muestran en el diagrama. En el ejemplo, cada canción tiene un título y un género, pero solo el valor del título se muestra en el diagrama.

## <a name="reference-relationships"></a>Relaciones de referencia
 Una relación de referencia representa cualquier tipo de relación que no se incrusta.

 Las relaciones de referencia se muestran normalmente en un diagrama como conectores entre formas.

 En la representación XML del modelo, se representa un vínculo de referencia entre dos elementos mediante *monikers.* Es decir, los monikers son nombres que identifican de forma única cada elemento del modelo. El nodo XML de cada elemento del modelo contiene un nodo que especifica el nombre de la relación y el moniker del otro elemento.

## <a name="roles"></a>Roles
 Cada relación de dominio tiene dos roles, un rol de origen y un rol de destino.

 En la siguiente imagen, la línea entre la clase de dominio del **publicador** y la relación de dominio **PublisherCatalog** es el rol de origen. La línea entre la relación de dominio y la clase de dominio **album** es el rol de destino.

 ![Roles y propiedades.](../modeling/media/propertycode.png "PropertyCode")

 Los nombres asociados a una relación son especialmente importantes cuando se escribe código de programa que atraviesa el modelo. Por ejemplo, al compilar la solución DSL, el publicador de la clase generada tiene un catálogo de propiedades que es una colección de álbumes. La clase album tiene un publicador de propiedades que es una única instancia del publicador de clases.

 Cuando se crea una relación en una definición de DSL, se proporcionan los valores predeterminados a los nombres de propiedad y de relación. Sin embargo, puede cambiarlos.

## <a name="multiplicities"></a>Multiplicidades
 Las multiplicidades especifican el número de elementos que pueden tener el mismo rol en una relación de dominio. En el ejemplo, la configuración de multiplicidad de cero a varios (0.. \*) en el rol de **Catálogo** especifica que cualquier instancia de la clase de dominio del **publicador** puede tener tantos vínculos de relación **PublisherCatalog** como desee.

 Configure la multiplicidad de un rol; para ello, escriba en el diagrama o modifique la propiedad `Multiplicity` en la ventana **propiedades** . En la tabla siguiente se describe la configuración de esta propiedad.

|Tipo de multiplicidad|Descripción|
|-----------------------|-----------------|
|0.. * (de cero a varios)|Cada instancia de la clase de dominio puede tener varias instancias de la relación o ninguna instancia de la relación.|
|0.. 1 (cero a uno)|Cada instancia de la clase de dominio no puede tener más de una instancia de la relación ni instancias de la relación.|
|1.. 1 (uno)|Cada instancia de la clase de dominio puede tener una instancia de la relación. No se puede crear más de una instancia de esta relación desde cualquier instancia de la clase role. Si la validación está habilitada, aparecerá un error de validación cuando cualquier instancia de la clase de rol no tenga ninguna instancia de la relación.|
|1.. * (uno a varios)|Cada instancia de la clase en el rol que tiene esta multiplicidad puede tener varias instancias de la relación, y cada instancia debe tener al menos una instancia de la relación. Si la validación está habilitada, aparecerá un error de validación cuando cualquier instancia de la clase de rol no tenga ninguna instancia de la relación.|

## <a name="domain-relationships-as-classes"></a>Relaciones de dominio como clases
 Un vínculo se representa en el almacén como una instancia de LinkElement, que es una clase derivada de ModelElement. Puede definir estas propiedades en el diagrama del modelo de dominio en las relaciones de dominio.

 También puede establecer una relación entre el origen o el destino de otras relaciones. En el diagrama del modelo de dominio, haga clic con el botón secundario en la relación de dominio y, a continuación, haga clic en **Mostrar como clase**. Aparecerá un cuadro de clase adicional. Después, puede conectar relaciones con él.

 Puede definir una relación en parte mediante herencia, del mismo modo que con las clases de dominio. Seleccione la relación derivada y establezca **relación base** en el ventana Propiedades.

 Una relación derivada especializa su relación base. Las clases de dominio a las que se vincula deben derivarse o ser iguales que las clases vinculadas por la relación base. Cuando se crea un vínculo de la relación derivada en un modelo, se trata de una instancia de las relaciones derivadas y base. En el código del programa, puede navegar hasta el final opuesto del vínculo mediante las propiedades generadas por la base o por la clase derivada.

## <a name="see-also"></a>Vea también
 [Relaciones de dominio en la API generada](../misc/domain-relationships-in-the-generated-api.md) [herramientas del lenguaje específico de dominio Glosario](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
