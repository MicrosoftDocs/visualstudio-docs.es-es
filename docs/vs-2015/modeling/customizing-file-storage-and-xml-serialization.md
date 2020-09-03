---
title: Personalización de la serialización File Storage y XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
ms.assetid: 76c53ef1-e3b9-45da-b425-1bddb3c01395
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0af30f31e7ee63c521a3a7c1acbafbb1cd109832
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548023"
---
# <a name="customizing-file-storage-and-xml-serialization"></a>Personalizar el almacenamiento de archivos y la serialización XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando el usuario guarda una instancia, o *modelo*, de un lenguaje específico de dominio (DSL) en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , se crea o se actualiza un archivo XML. Se puede volver a cargar el archivo para volver a crear el modelo en el almacén.

 Puede personalizar el esquema de serialización ajustando los valores de **comportamiento de serialización XML** en el explorador de DSL. Hay un nodo en el **comportamiento de serialización XML** para cada clase de dominio, propiedad y relación. Las relaciones se encuentran en sus clases de origen. También hay nodos correspondientes a las clases de forma, conector y diagrama.

 También puede escribir código de programa para una personalización más avanzada.

> [!NOTE]
> Si desea guardar el modelo en un formato determinado, pero no necesita volver a cargarlo desde ese formulario, considere la posibilidad de usar plantillas de texto para generar la salida del modelo, en lugar de un esquema de serialización personalizado. Para obtener más información, vea [generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Archivos de modelos y diagramas
 Normalmente, cada modelo se guarda en dos archivos:

- El archivo de modelo tiene un nombre como **Model1. midsl**. Almacena los elementos del modelo y las relaciones y sus propiedades. La extensión de archivo como **. midsl** viene determinada por la propiedad **FileExtension** del nodo **Editor** en la definición de DSL.

- El archivo de diagrama tiene un nombre como **Model1. midsl. diagram**. Almacena las formas, conectores y sus posiciones, colores, grosores de línea y otros detalles de la apariencia del diagrama. Si el usuario elimina un archivo **. diagram** , no se pierde la información esencial del modelo. Solo se pierde el diseño del diagrama. Cuando se abra el archivo de modelo, se creará un conjunto predeterminado de formas y conectores.

#### <a name="to-change-the-file-extension-of-a-dsl"></a>Para cambiar la extensión de un archivo DSL

1. Abra la definición de DSL. En el explorador de DSL, haga clic en el nodo editor.

2. En el ventana Propiedades, edite la propiedad **FileExtension** . No incluya el "." inicial de la extensión de nombre de archivo.

3. En Explorador de soluciones, cambie el nombre de los dos archivos de plantilla de elemento en **DslPackage\ProjectItemTemplates**. Estos archivos tienen nombres que siguen este formato:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>El esquema de serialización predeterminado
 Para crear un ejemplo de este tema, se usó la siguiente definición de DSL.

 ![Diagrama de definición de DSL &#45; modelo de árbol de familia](../modeling/media/familyt-person.png "FamilyT_Person")

 Este DSL se usó para crear un modelo que tenga la apariencia siguiente en la pantalla.

 ![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt-instance.png "FamilyT_Instance")

 Este modelo se guardó y se volvió a abrir en el editor de texto XML:

```
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>

```

 Tenga en cuenta los siguientes puntos sobre el modelo serializado:

- Cada nodo XML tiene un nombre que es igual que el nombre de una clase de dominio, excepto en que la letra inicial está en minúsculas. Por ejemplo, `familyTreeModel` y `person`.

- Las propiedades de dominio como Name y BirthYear se serializan como atributos en los nodos XML. De nuevo, el carácter inicial del nombre de la propiedad se convierte a minúsculas.

- Cada relación se serializa como un nodo XML anidado dentro del extremo de origen de la relación. El nodo tiene el mismo nombre que la propiedad de rol de origen, pero con un carácter inicial en minúscula.

     Por ejemplo, en la definición de DSL, un rol denominado **People** se encuentra en la clase **familytree** .  En el XML, se representa mediante el nodo denominado `people` anidado dentro del `familyTreeModel` nodo.

- El extremo de destino de cada relación de incrustación se serializa como un nodo anidado en la relación. Por ejemplo, el `people` nodo contiene varios `person` nodos.

- El extremo de destino de cada relación de referencia se serializa como un *moniker*, que codifica una referencia al elemento de destino.

     Por ejemplo, en un `person` nodo, puede haber una `children` relación. Este nodo contiene monikers como:

    ```
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understanding-monikers"></a>Descripción de los monikers
 Los monikers se utilizan para representar referencias cruzadas entre diferentes partes de los archivos de diagrama y de modelo. También se usan en el `.diagram` archivo para hacer referencia a los nodos del archivo de modelo. Hay dos formas de moniker:

- El *identificador de monikers* es el GUID del elemento de destino. Por ejemplo:

  ```
  <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />

  ```

- Los *monikers de clave calificados* identifican el elemento de destino por el valor de una propiedad de dominio designada denominada clave de moniker. El moniker del elemento de destino va precedido por el moniker de su elemento primario en el árbol de relaciones de incrustación.

   Los ejemplos siguientes se toman de un DSL en el que hay una clase de dominio denominada album, que tiene una relación de incrustación con una clase de dominio denominada Song:

  ```
  <albumMoniker title="/My Favorites/Jazz after Teatime" />
  <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />

  ```

   Los monikers de clave calificados se usarán si la clase de destino tiene una propiedad de dominio para la que la opción **es la clave de moniker** establecida `true` en en el **comportamiento de serialización XML**. En el ejemplo, esta opción se establece para las propiedades de dominio denominadas "title" en las clases de dominio "album" y "Song".

  Los monikers de clave calificados son más fáciles de leer que los de ID. Si desea que los usuarios lean el XML de los archivos de modelo, considere la posibilidad de usar monikers de clave calificados. Sin embargo, el usuario puede establecer más de un elemento para que tenga la misma clave de moniker. Las claves duplicadas pueden provocar que el archivo no se recargue correctamente. Por lo tanto, si define una clase de dominio a la que se hace referencia mediante monikers de clave calificados, debe tener en cuenta las formas de evitar que el usuario guarde un archivo con monikers duplicados.

#### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Para establecer una clase de dominio a la que hagan referencia los monikers de identificador

1. Asegúrese de que la **clave de moniker** es `false` para cada propiedad de dominio de la clase y sus clases base.

    1. En DSL Explorer, expanda **XML Serialization Behavior\Class \\ Data** _\<the domain class>_ **\Element Data**.

    2. Compruebe que la **clave de moniker** es `false` para cada propiedad de dominio.

    3. Si la clase de dominio tiene una clase base, repita el procedimiento en esa clase.

2. Establezca el **identificador de serialización**  =  `true` para la clase de dominio.

     Esta propiedad se puede encontrar en **comportamiento de serialización XML**.

#### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Para establecer una clase de dominio a la que hagan referencia los monikers de clave calificados

- Set **es la clave de moniker** para una propiedad de dominio de una clase de dominio existente. El tipo de la propiedad debe ser `string` .

    1. En DSL Explorer, expanda **XML Serialization Behavior\Class \\ Data** _\<the domain class>_ **\Element Data**y, a continuación, seleccione la propiedad domain.

    2. En el ventana Propiedades, establezca la **clave de moniker** en `true` .

- \- o -

     Cree una nueva clase de dominio mediante la herramienta de **clase de dominio con nombre** .

     Esta herramienta crea una nueva clase que tiene una propiedad de dominio denominada Name. El **nombre de elemento es** y las propiedades de **clave de moniker** de esta propiedad de dominio se inicializan en `true` .

- \- o -

     Cree una relación de herencia desde la clase de dominio a otra clase que tenga una propiedad de clave de moniker.

### <a name="avoiding-duplicate-monikers"></a>Evitar monikers duplicados
 Si utiliza monikers de clave calificados, es posible que dos elementos del modelo de un usuario tengan el mismo valor en la propiedad de clave. Por ejemplo, si el DSL tiene una clase Person que tiene un nombre de propiedad, el usuario podría establecer los nombres de dos elementos en el mismo. Aunque el modelo se puede guardar en el archivo, no se volvería a cargar correctamente.

 Hay varios métodos que ayudan a evitar esta situación:

- Set **es**  =  `true` un nombre de elemento para la propiedad de dominio Key. Seleccione la propiedad dominio en el diagrama de definición de DSL y, a continuación, establezca el valor en el ventana Propiedades.

     Cuando el usuario crea una nueva instancia de la clase, este valor hace que se asigne automáticamente un valor diferente a la propiedad de dominio. El comportamiento predeterminado agrega un número al final del nombre de la clase. Esto no impide que el usuario cambie el nombre por un duplicado, pero lo ayuda en el caso de que el usuario no establezca el valor antes de guardar el modelo.

- Habilite la validación para DSL. En el explorador de DSL, seleccione Editor\Validation y establezca las propiedades **use...** en `true` .

     Hay un método de validación generado automáticamente que comprueba las ambigüedades. El método está en la `Load` categoría validación. Esto garantiza que se advierte al usuario de que es posible que no sea posible volver a abrir el archivo.

     Para obtener más información, vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Rutas de acceso y calificadores de moniker
 Un moniker de clave calificado finaliza con la clave de moniker y tiene como prefijo el moniker de su elemento primario en el árbol de incrustación. Por ejemplo, si el moniker de un álbum es:

```
<albumMoniker title="/My Favorites/Jazz after Teatime" />

```

 Después, una de las canciones de ese álbum podría ser:

```
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

 Sin embargo, si en su lugar se hace referencia a los álbumes mediante el identificador, los monikers serían como sigue:

```
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

 Tenga en cuenta que, dado que un GUID es único, nunca se antepone por el moniker de su elemento primario.

 Si sabe que una propiedad de dominio determinada siempre tendrá un valor único dentro de un modelo, puede establecer el **calificador de moniker** en `true` para esa propiedad. Esto hará que se use como calificador, sin utilizar el moniker del elemento primario. Por ejemplo, si establece both como **calificador de moniker** y **es la clave de moniker** para la propiedad de dominio title de la clase album, el nombre o el identificador del modelo no se utiliza en monikers para album y sus elementos secundarios incrustados:

```
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />

```

## <a name="customizing-the-structure-of-the-xml"></a>Personalizar la estructura del XML
 Para hacer las personalizaciones siguientes, expanda el nodo **comportamiento de serialización XML** en el explorador de DSL. En una clase de dominio, expanda el nodo datos de elemento para ver la lista de propiedades y relaciones que se encuentran en esta clase. Seleccione una relación y ajuste sus opciones en el ventana Propiedades.

- Establezca el **elemento omitir** en true para omitir el nodo de rol de origen y no solo la lista de elementos de destino. No debe establecer esta opción si hay más de una relación entre las clases de origen y de destino.

    ```

    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>

    ```

- Establezca **usar formulario completo** para insertar los nodos de destino en los nodos que representan las instancias de la relación. Esta opción se establece automáticamente cuando se agregan propiedades de dominio a una relación de dominio.

    ```

    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>

    ```

- Establezca **Representation**  =  el**elemento** de representación para tener una propiedad de dominio guardada como un elemento en lugar de como un valor de atributo.

    ```
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Para cambiar el orden en el que se serializan los atributos y las relaciones, haga clic con el botón secundario en un elemento bajo datos de elemento y use los comandos de menú **subir** o **bajar** .

## <a name="major-customization-using-program-code"></a>Personalización principal con código de programa
 Puede reemplazar partes o todos los algoritmos de serialización.

 Se recomienda que estudie el código de **Dsl\Generated Code\Serializer.CS** y **SerializationHelper.CS**.

#### <a name="to-customize-the-serialization-of-a-particular-class"></a>Para personalizar la serialización de una clase determinada

1. Set **es personalizado** en el nodo de esa clase en el **comportamiento de serialización XML**.

2. Transformar todas las plantillas, compilar la solución e investigar los errores de compilación resultantes. Los comentarios cercanos a cada error explican qué código debe proporcionar.

#### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Para proporcionar su propia serialización para todo el modelo

1. Métodos de invalidación en Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opciones en el comportamiento de serialización XML
 En DSL Explorer, el nodo comportamiento de serialización XML contiene un nodo secundario para cada clase de dominio, relación, forma, conector y clase de diagrama. En cada uno de esos nodos hay una lista de propiedades y relaciones cuyo origen se encuentra en ese elemento. Las relaciones se representan en su propio derecho y en las clases de origen.

 En la tabla siguiente se resumen las opciones que se pueden establecer en esta sección de la definición de DSL. En cada caso, seleccione un elemento en DSL Explorer y establezca las opciones en el ventana Propiedades.

### <a name="xml-class-data"></a>Datos de clase XML
 Estos elementos se encuentran en el explorador de DSL, en **serialización XML Behavior\Class Data**.

|Propiedad|Descripción|
|-|-|
|Tiene un esquema de elemento personalizado|Si es true, indica que la clase de dominio tiene un esquema de elemento personalizado|
|Personalizado|Establézcalo en **true** si desea escribir su propio código de serialización y deserialización para esta clase de dominio.<br /><br /> Compile la solución e investigue los errores para detectar instrucciones detalladas.|
|Clase de dominio|Clase de dominio a la que se aplica este nodo de datos de clase. Sólo lectura.|
|Nombre del elemento|Nombre del nodo XML para los elementos de esta clase. El valor predeterminado es una versión en minúsculas del nombre de la clase de dominio.|
|Nombre del atributo de moniker|Nombre del atributo que se usa en los elementos de moniker para contener la referencia. Si está en blanco, se usa el nombre de la propiedad de clave o el identificador.<br /><br /> En este ejemplo, es "Name":  `<personMoniker name="/Mike Nash"/>`|
|Nombre del elemento de moniker|Nombre del elemento XML utilizado para los monikers que hacen referencia a los elementos de esta clase.<br /><br /> El valor predeterminado es una versión en minúsculas del nombre de clase con el sufijo "moniker". Por ejemplo, `personMoniker`.|
|Nombre de tipo de moniker|Nombre del tipo XSD generado para los monikers para los elementos de esta clase. El XSD está en **Dsl\Generated code \\ \* Schema. xsd**|
|Serializar identificador|Si es true, el GUID del elemento se incluye en el archivo. Debe ser true si no hay ninguna propiedad marcada como clave de **moniker** y el DSL define las relaciones de referencia con esta clase.|
|Nombre del tipo|Nombre del tipo XML generado en el XSD de la clase de dominio designada.|
|Notas|Notas informales asociadas a este elemento|

### <a name="xml-property-data"></a>Datos de propiedad XML
 Los nodos de propiedad XML se encuentran en los nodos de clase.

|Propiedad|Descripción|
|-|-|
|Propiedad de dominio|Propiedad a la que los datos de configuración de serialización de XML se aplican. Sólo lectura.|
|Clave de moniker|Si es true, la propiedad se utiliza como clave para crear monikers que hacen referencia a las instancias de esta clase de dominio.|
|Calificador de moniker|Si es True, la propiedad se usa para crear el calificador en monikers. Si es false, y si SerializeId no es true para esta clase de dominio, el moniker del elemento primario en el árbol de incrustación calificará los monikers.|
|Representación|Si es un atributo, la propiedad se serializará como un atributo XML; si es un elemento, se serializa como elemento; si se omite, no se serializará.|
|Nombre XML|Nombre utilizado para el atributo o elemento XML que representa la propiedad. De forma predeterminada, se trata de una versión en minúsculas del nombre de la propiedad de dominio.|
|Notas|Notas informales asociadas a este elemento|

### <a name="xml-role-data"></a>Datos de rol XML
 Los nodos de datos de rol se encuentran en los nodos de clase de origen.

|Propiedad|Descripción|
|--------------|-----------------|
|Tiene un moniker personalizado|Establézcalo en true si desea proporcionar su propio código para generar y resolver monikers que atraviesan esta relación.<br /><br /> Para obtener instrucciones detalladas, compile la solución y, a continuación, haga doble clic en los mensajes de error.|
|Relación de dominio|Especifica la relación a la que se aplican estas opciones. Sólo lectura.|
|Omitir elemento|Si es true, el nodo XML que se corresponde con el rol de origen se omite en el esquema.<br /><br /> Si hay más de una relación entre las clases de origen y de destino, este nodo de rol distingue entre los vínculos que pertenecen a las dos relaciones. Por lo tanto, se recomienda que no establezca esta opción en este caso.|
|Nombre del elemento role|Especifica el nombre del elemento XML que se deriva del rol de origen. El valor predeterminado es el nombre de la propiedad de rol.|
|Usar formulario completo|Si es true, cada elemento o moniker de destino se incluye en un nodo XML que representa la relación. Debe establecerse en true si la relación tiene sus propias propiedades de dominio.|

## <a name="see-also"></a>Consulte también
 [Navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md) que [genera código a partir de un lenguaje específico del dominio](../modeling/generating-code-from-a-domain-specific-language.md)
