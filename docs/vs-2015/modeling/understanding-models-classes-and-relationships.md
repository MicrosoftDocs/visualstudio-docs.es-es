---
title: Descripción de los modelos, las clases y relaciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
ms.assetid: 2ecd569c-b369-41ea-b78e-a61b62e2e4e9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 678e7a9c32f8c69e9f0bac5ebc3a077e7e625771
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999770"
---
# <a name="understanding-models-classes-and-relationships"></a>Introducción a los modelos, las clases y las relaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un lenguaje específico de dominio (DSL) se define mediante su archivo de definición de DSL, junto con cualquier código de programa personalizado que se haya escrito. La mayoría del código de programa en la solución de DSL se genera a partir de este archivo.  
  
 En este tema se explica las características principales de la definición de DSL.  
  
## <a name="the-dsl-definition"></a>La definición de DSL  
 Al abrir `Dsl\DslDefinition.dsl`, su [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ventana similar a la siguiente imagen.  
  
 ![diseñador dsl](../modeling/media/dsl-designer.png "dsl_designer")  
  
 La información más importante en la definición de DSL se muestra en el diagrama de definición de DSL. Obtener información adicional, que también forma parte de DslDefinition.dsl, se muestra en el Explorador de DSL, que normalmente aparece en el lado del diagrama. Trabajar con el diagrama para las tareas más frecuentes y con el Explorador de DSL para las personalizaciones más avanzadas.  
  
 El diagrama de definición de DSL muestra las clases de dominio que definen los elementos del modelo y las relaciones que definen vínculos entre elementos de modelo. También muestra las formas y conectores que se usan para mostrar los elementos del modelo al usuario.  
  
 ![diseñador dsl con carril](../modeling/media/dsl-desinger.png "dsl_desinger")  
  
 Cuando se selecciona un elemento en la definición de DSL, en el diagrama o en el Explorador de DSL, se muestra información sobre él en la ventana Propiedades. Información adicional puede mostrarse en la ventana Detalles de DSL.  
  
### <a name="models-are-instances-of-dsls"></a>Los modelos son instancias de DSL  
 Un *modelo* es una instancia de DSL creada por un usuario. Un modelo contiene los elementos del modelo, que son instancias de las clases de dominio que definen y vínculos entre los elementos, que son instancias de las relaciones de dominio que defina. También puede tener un modelo de formas y conectores que mostrar los elementos del modelo y los vínculos en un diagrama. La definición de DSL incluye las clases de forma, las clases de conector y una clase para el diagrama.  
  
 Una definición de DSL es también se denomina un *modelo de dominio*. Un modelo de definición de DSL o de dominio es la representación en tiempo de diseño del lenguaje específico de dominio, mientras que el modelo es la creación de instancias de tiempo de ejecución del lenguaje específico de dominio.  
  
## <a name="domain-classes-define-model-elements"></a>Las clases de dominio definen los elementos del modelo  
 Clases de dominio se utilizan para crear los distintos elementos en el dominio y las relaciones de dominio son los vínculos entre los elementos. Son la representación en tiempo de diseño de los elementos y vínculos que se crearán instancias por los usuarios del lenguaje de diseño específicos al crear sus modelos.  
  
 En esta ilustración se muestra un modelo que se ha creado por el usuario de una biblioteca de música DSL. Álbumes de música se representan mediante los cuadros que contienen listas de canciones. Los artistas se representan mediante los cuadros de esquinas redondeadas y están conectados a los álbumes a la que han contribuido con.  
  
 ![Modelo de instancia de DSL generado](../modeling/media/music-instance.png "Music_Instance")  
  
 La definición de DSL separa dos aspectos. La apariencia de los elementos del modelo en el diagrama del modelo se define mediante el uso de las clases de formas y las clases de conector. La información que lleva en el modelo se define mediante las clases de dominio y relaciones de dominio.  
  
 La siguiente ilustración muestra las clases de dominio y relaciones en la definición de DSL de la biblioteca de música.  
  
 ![Relaciones de incrustación y referencia](../modeling/media/music-classes.png "Music_Classes")  
  
 La ilustración muestra cuatro clases de dominio: Música, álbum, artista y canción. Las clases de dominio definen las propiedades de dominio como nombre, título y así sucesivamente. En el modelo de instancia, los valores de algunas de estas propiedades se muestran en el diagrama.  
  
 Entre las clases son las relaciones de dominio: MusicHasAlbums, MusicHasArtists, AlbumbHasSongs y ArtistAppearedOnAlbums. Las relaciones tienen multiplicidades como 1..1, 0.. *. Por ejemplo, todas las canciones deben estar relacionado con exactamente un álbum a través de la relación AlbumHasSongs. Cada álbum puede tener cualquier número de canciones.  
  
### <a name="rearranging-the-dsl-definition-diagram"></a>Reorganizar el diagrama de definición de DSL  
 Tenga en cuenta que una clase de dominio puede aparecer varias veces en el diagrama de definición de DSL, como álbum en esta imagen. Siempre hay una vista principal, y puede haber algunos *referencia* vistas.  
  
 Para reorganizar el diagrama de definición de DSL, hacer lo siguiente:  
  
-   Intercambiar principal y hacer referencia a vistas mediante el **Traer árbol aquí** y **dividir árbol** comandos. Haga clic en una clase de dominio único para ver estos comandos.  
  
-   Cambiar el orden de las clases de dominio y las clases de formas presionando Ctrl + arriba y Ctrl+flecha abajo.  
  
-   Contraer o expandir las clases mediante el icono en la superior derecha de cada forma.  
  
-   Contraer partes del árbol, haga clic en el signo menos (-) en la parte inferior de una clase de dominio.  
  
## <a name="inheritance"></a>Herencia  
 Clases de dominio se pueden definir mediante herencia. Para crear una derivación de herencia, haga clic en la herramienta de herencia, haga clic en la clase derivada y, a continuación, haga clic en la clase base. Un elemento de modelo tiene todas las propiedades que se definen en su propia clase de dominio, junto con todas las propiedades heredadas de la clase base. También hereda sus roles en las relaciones.  
  
 También puede utilizarse la herencia entre las relaciones, formas y conectores. Herencia debe mantener en el mismo grupo. Una forma no puede heredar de una clase de dominio.  
  
## <a name="domain-relationships"></a>Relaciones de dominio  
 Los elementos del modelo se pueden vincular mediante relaciones. Vínculos siempre son binarios; se vinculan exactamente dos elementos. Sin embargo, cualquier elemento puede tener muchos vínculos a otros objetos, y que incluso puede haber más de un vínculo entre el mismo par de elementos.  
  
 Tal como se puede definir diferentes clases de elementos, puede definir diferentes clases de vínculos. Se llama a la clase de un vínculo a un *relación de dominio*. Una relación de dominio especifica qué clases de elemento se pueden conectar sus instancias. Se llama a cada extremo de una relación de un *rol*, y la relación de dominio define los nombres de los dos roles, así como para la propia relación.  
  
 Hay dos tipos de relaciones de dominio: inserción de relaciones y relaciones de referencia. En el diagrama de definición de DSL, las relaciones de incrustación tienen líneas sólidas en cada rol y las relaciones de referencia han líneas de guiones.  
  
### <a name="embedding-relationships"></a>Las relaciones de incrustación  
 Todos los elementos de un modelo, excepto su raíz, es el destino de un vínculo de incrustación. Por lo tanto, todo el modelo conforma un único árbol de incrustación de vínculos. Una relación de incrustación representa la propiedad o contención. Dos elementos de modelo que están relacionados de esta manera son también conocido como primarios y secundarios. Se dice que el elemento secundario incrustado en el elemento primario.  
  
 Vínculos de incrustación no normalmente aparecen explícitamente como conectores en un diagrama. En su lugar, normalmente se representan por contención. La raíz del modelo se representa mediante el diagrama y elementos incrustados en ella se muestran como formas del diagrama.  
  
 En el ejemplo, la clase raíz Music tiene una relación de incrustación MusicHasAlbums al álbum, que tiene una incrustación AlbumHasSongs canción. Las canciones se muestran como elementos de una lista dentro de cada álbum. Música también tiene una incrustación MusicHasArtists a la clase del intérprete, cuyas instancias también aparecen como formas del diagrama.  
  
 De forma predeterminada, los elementos incrustados se eliminan automáticamente cuando se eliminan sus elementos primarios.  
  
 Cuando se guarda un modelo de archivos en formato XML, elementos incrustados están anidados dentro de sus elementos primarios, a menos que haya personalizado la serialización.  
  
> [!NOTE]
>  Incrustación no es lo mismo que herencia. Los elementos secundarios en una relación de incrustación no heredan las propiedades del elemento primario. Una inclusión es un tipo de vínculo entre elementos de modelo. La herencia es una relación entre las clases y no crea vínculos entre elementos de modelo.  
  
### <a name="embedding-rules"></a>Reglas de incrustación  
 Todos los elementos de un modelo de instancia deben ser el destino de exactamente un vínculo de incrustación, excepto la raíz del modelo.  
  
 Por lo tanto, cada clase de dominio de no abstracta, excepto la clase raíz, debe ser el destino de al menos una relación de incrustación, o deben heredar de inclusión de una clase base. Una clase puede ser el destino de incrustaciones de dos o más, pero sus elementos de modelo de instancia solo pueden tener un elemento primario a la vez. La multiplicidad del destino al origen debe ser de 0.. 1 o 1.. 1.  
  
### <a name="the-explorer-displays-the-embedding-tree"></a>El explorador muestra el árbol de incrustación  
 La definición de DSL crea también un explorador, lo que ven los usuarios junto con su diagrama del modelo.  
  
 ![Explorador generado de DSL](../modeling/media/music-explorer.png "Music_Explorer")  
  
 El explorador muestra todos los elementos en el modelo, incluso aquellos que no ha definido ninguna forma. Muestra los elementos y relaciones de incrustación, pero no hacer referencia a las relaciones.  
  
 Para ver los valores de las propiedades de dominio de un elemento, el usuario selecciona un elemento, en el diagrama del modelo o en el Explorador de modelos y abre la ventana Propiedades. Muestra todas las propiedades de dominio, los que no se muestran en el diagrama incluidos. En el ejemplo, cada canción tiene un título y un género, pero solo el valor del título se muestra en el diagrama.  
  
## <a name="reference-relationships"></a>Relaciones de referencia  
 Una relación de referencia representa cualquier tipo de relación que no se insertan.  
  
 Las relaciones de referencia normalmente se muestran en un diagrama como conectores entre las formas.  
  
 En la representación XML del modelo, un vínculo de referencia entre dos elementos que se representa mediante *monikers.* Es decir, los monikers son nombres que identifican de forma única cada elemento en el modelo. El nodo XML para cada elemento del modelo contiene un nodo que especifica el nombre de la relación y el moniker del otro elemento.  
  
## <a name="roles"></a>Roles  
 Cada relación de dominio tiene dos funciones, un rol de origen y un rol de destino.  
  
 En la siguiente imagen, la línea entre el **Publisher** la clase de dominio y el **PublisherCatalog** relación de dominio es el rol de origen. La línea entre la relación de dominio y el **álbum** la clase de dominio es el rol de destino.  
  
 ![Las funciones y propiedades. ](../modeling/media/propertycode.png "PropertyCode")  
  
 Los nombres asociados con una relación son especialmente importantes al escribir código de programa que recorre el modelo. Por ejemplo, al compilar la solución de DSL, el publicador de la clase generada tiene una propiedad de catálogo que es una colección de álbumes. La clase álbum tiene una publicador que es una única instancia de la clase de publicador de la propiedad.  
  
 Al crear una relación en una definición de DSL, los nombres de propiedad y la relación se proporcionan los valores predeterminados. Sin embargo, puede cambiarlos.  
  
## <a name="multiplicities"></a>Multiplicidades  
 Multiplicidades especifican cuántos elementos puede tener el mismo rol en una relación de dominio. En el ejemplo, el cero a varios (0..\*) valor de multiplicidad en el **catálogo** rol especifica que cualquier instancia de la **Publisher** la clase de dominio puede tener tantos  **PublisherCatalog** vínculos de relación como desee darle.  
  
 Configurar la multiplicidad de un rol escribiendo en el diagrama o modificando el `Multiplicity` propiedad en el **propiedades** ventana. En la tabla siguiente se describe la configuración de esta propiedad.  
  
|Tipo de multiplicidad|Descripción|  
|-----------------------|-----------------|  
|0.. * (de cero a muchos)|Cada instancia de la clase de dominio puede tener varias instancias de la relación o ninguna instancia de la relación.|  
|(De cero a uno) de 0.. 1|Cada instancia de la clase de dominio puede tener ninguna instancia de la relación o de no más de una instancia de la relación.|  
|1..1 (uno)|Cada instancia de la clase de dominio puede tener una instancia de la relación. No se puede crear más de una instancia de esta relación desde cualquier instancia de la clase de función. Si está habilitada la validación, aparecerá un error de validación cuando cualquier instancia de la clase de función no tiene ninguna instancia de la relación.|  
|1.. * (uno a varios)|Cada instancia de la clase en el rol que tiene esta multiplicidad puede tener varias instancias de la relación, y cada instancia debe tener al menos una instancia de la relación. Si está habilitada la validación, aparecerá un error de validación cuando cualquier instancia de la clase de función no tiene ninguna instancia de la relación.|  
  
## <a name="domain-relationships-as-classes"></a>Relaciones de dominio como clases  
 Un vínculo se representa en el Store como una instancia de LinkElement, que es una clase derivada de ModelElement. Puede definir estas propiedades en el diagrama del modelo de dominio en las relaciones de dominio.  
  
 También puede establecer una relación el origen o destino de otras relaciones. En el diagrama de modelo de dominio, haga clic en la relación de dominio y, a continuación, haga clic en **mostrar como clase**. Se mostrará un cuadro de clase adicional. Las relaciones, a continuación, puede conectarse a él.  
  
 Puede definir una relación parte por herencia, se puede hacer con las clases de dominio. Seleccione la relación derivada y establezca **relación Base** en la ventana Propiedades.  
  
 Una relación derivada especializa su relación base. El dominio de las clases que TI vínculos deben derivarse de o igual que las clases vinculadas mediante la relación base. Cuando se crea un vínculo de la relación derivada de un modelo, es una instancia de la clase derivada y las relaciones bases. En el código de programa, puede navegar con el extremo opuesto del vínculo mediante las propiedades generadas por la base o la clase derivada.  
  
## <a name="see-also"></a>Vea también  
 [Relaciones de dominio en la API generada](../misc/domain-relationships-in-the-generated-api.md)   
 [Glosario de las Herramientas del lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
