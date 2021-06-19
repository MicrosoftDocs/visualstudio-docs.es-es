---
title: Personalizar el almacenamiento de archivos y la serialización XML
description: Obtenga información sobre el archivo XML creado o actualizado al guardar una instancia, o modelo, de un lenguaje específico de dominio (DSL) en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b3026010e37108ca1b19096d48a3c8d88ab6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389376"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personalizar el almacenamiento de archivos y la serialización XML

Cuando el usuario guarda una instancia, o modelo *,* de un lenguaje específico de dominio (DSL) en Visual Studio, se crea o actualiza un archivo XML. El archivo se puede volver a cargar para volver a crear el modelo en store.

Puede personalizar el esquema de serialización ajustando la configuración en **Comportamiento de serialización xml** en el Explorador dsl. Hay un nodo en **Comportamiento de serialización xml** para cada clase de dominio, propiedad y relación. Las relaciones se encuentran en sus clases de origen. También hay nodos correspondientes a las clases de forma, conector y diagrama.

También puede escribir código de programa para una personalización más avanzada.

> [!NOTE]
> Si desea guardar el modelo en un formato determinado, pero no necesita volver a cargarlo desde ese formulario, considere la posibilidad de usar plantillas de texto para generar la salida del modelo, en lugar de un esquema de serialización personalizado. Para obtener más información, vea [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Archivos de diagrama y modelo

Cada modelo normalmente se guarda en dos archivos:

- El archivo de modelo tiene un nombre como **Model1.mydsl.** Almacena los elementos y relaciones del modelo y sus propiedades. La extensión de archivo como **.mydsl** viene determinada por la propiedad **FileExtension** del **nodo Editor** en la definición de DSL.

- El archivo de diagrama tiene un nombre como **Model1.mydsl.diagram.** Almacena las formas, conectores y sus posiciones, colores, grosores de línea y otros detalles de la apariencia del diagrama. Si el usuario elimina un **archivo .diagram,** no se pierde la información esencial del modelo. Solo se pierde el diseño del diagrama. Cuando se abra el archivo de modelo, se creará un conjunto predeterminado de formas y conectores.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Para cambiar la extensión de archivo de un DSL

1. Abra la definición de DSL. En el Explorador de DSL, haga clic en el nodo Editor.

2. En la ventana Propiedades, edite la **propiedad FileExtension.** No incluya el "." inicial de la extensión de nombre de archivo.

3. En Explorador de soluciones, cambie el nombre de los dos archivos de plantilla de elemento en **DslPackage\ProjectItemTemplates**. Estos archivos tienen nombres que siguen este formato:

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>El esquema de serialización predeterminado

Para crear un ejemplo para este tema, se usó la siguiente definición de DSL.

![Diagrama de definición de DSL &#45; modelo de árbol de familia](../modeling/media/familyt_person.png)

Este DSL se usó para crear un modelo que tiene la siguiente apariencia en la pantalla.

![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt_instance.png)

Este modelo se guardó y, a continuación, se abrió de nuevo en el editor de texto XML:

```xml
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

Observe los siguientes puntos sobre el modelo serializado:

- Cada nodo XML tiene un nombre que es el mismo que un nombre de clase de dominio, salvo que la letra inicial está en minúsculas. Por ejemplo, `familyTreeModel` y `person`.

- Las propiedades de dominio como Name y BirthYear se serializan como atributos en los nodos XML. De nuevo, el carácter inicial del nombre de propiedad se convierte a minúsculas.

- Cada relación se serializa como un nodo XML anidado dentro del extremo de origen de la relación. El nodo tiene el mismo nombre que la propiedad de rol de origen, pero con un carácter inicial en minúsculas.

     Por ejemplo, en la definición de DSL, un rol denominado **People** se proporciona en la **clase FamilyTree.**  En xml, esto se representa mediante el nodo denominado `people` anidado dentro del `familyTreeModel` nodo.

- El extremo de destino de cada relación de inserción se serializa como un nodo anidado en la relación. Por ejemplo, el `people` nodo contiene varios `person` nodos.

- El extremo de destino de cada relación de referencia se serializa como *un moniker*, que codifica una referencia al elemento de destino.

     Por ejemplo, en `person` un nodo, puede haber una `children` relación. Este nodo contiene monikers como:

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Información sobre Monikers

Los monikers se usan para representar referencias cruzadas entre diferentes partes del modelo y los archivos de diagrama. También se usan en el `.diagram` archivo para hacer referencia a los nodos del archivo de modelo. Hay dos formas de moniker:

- *Los monikers de identificador* citan el GUID del elemento de destino. Por ejemplo:

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *Los monikers de clave* calificados identifican el elemento de destino por el valor de una propiedad de dominio designada denominada clave de moniker. El moniker del elemento de destino tiene como prefijo el moniker de su elemento primario en el árbol de relaciones de inserción.

     Los ejemplos siguientes se toman de un DSL en el que hay una clase de dominio denominada Album, que tiene una relación de incrustación con una clase de dominio denominada Song:

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Se usarán monikers de clave calificados si la clase de destino tiene una propiedad de dominio para la que la opción **Is Moniker Key** está establecida en `true` en comportamiento de **serialización xml**. En el ejemplo, esta opción se establece para las propiedades de dominio denominadas "Title" en las clases de dominio "Album" y "Song".

Los monikers clave calificados son más fáciles de leer que los monikers de identificador. Si piensa que los usuarios lean el XML de los archivos de modelo, considere la posibilidad de usar monikers de clave calificados. Sin embargo, es posible que el usuario establezca más de un elemento para que tenga la misma clave de moniker. Las claves duplicadas podrían hacer que el archivo no se vuelva a cargar correctamente. Por lo tanto, si define una clase de dominio a la que se hace referencia mediante monikers de clave calificados, debe considerar formas de impedir que el usuario guarde un archivo que tenga monikers duplicados.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Para establecer una clase de dominio a la que hacen referencia los monikers de identificador

1. Asegúrese de que **Is Moniker Key** es `false` para cada propiedad de dominio de la clase y sus clases base.

    1. En el Explorador de DSL, expanda **Comportamiento de serialización XML\Datos de clase \\ \<the domain class> \Element Data**.

    2. Compruebe que **Is Moniker Key es** para cada propiedad de `false` dominio.

    3. Si la clase de dominio tiene una clase base, repita el procedimiento en esa clase.

2. Establezca **Serialize Id para** la clase de  =  `true` dominio.

     Esta propiedad se puede encontrar en **Comportamiento de serialización xml**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Para establecer una clase de dominio a la que hacen referencia los monikers clave calificados

- Establecer **es clave de moniker para** una propiedad de dominio de una clase de dominio existente. El tipo de la propiedad debe ser `string` .

    1. En el Explorador dsl, expanda **Comportamiento de serialización xml\Datos de clase \\ \<the domain class> \Datos** de elemento y, a continuación, seleccione la propiedad de dominio.

    2. En la ventana Propiedades, establezca **Is Moniker Key** en `true` .

- \- O bien

     Cree una nueva clase de dominio mediante la **herramienta Clase de dominio** con nombre.

     Esta herramienta crea una nueva clase que tiene una propiedad de dominio denominada Name. Las **propiedades Is Element Name** y Is **Moniker Key** de esta propiedad de dominio se inicializan en `true` .

- \- O bien

     Cree una relación de herencia de la clase de dominio a otra clase que tenga una propiedad de clave de moniker.

### <a name="avoid-duplicate-monikers"></a>Evitar monikers duplicados

Si usa monikers de clave calificados, es posible que dos elementos del modelo de un usuario puedan tener el mismo valor en la propiedad key. Por ejemplo, si el DSL tiene una clase Person que tiene una propiedad Name, el usuario podría establecer los nombres de dos elementos en el mismo. Aunque el modelo se podría guardar en el archivo, no se volverá a cargar correctamente.

Hay varios métodos que ayudan a evitar esta situación:

- Establecer **es el nombre del elemento** para la propiedad de dominio de  =  `true` clave. Seleccione la propiedad de dominio en el diagrama de definición de DSL y, a continuación, establezca el valor en el ventana Propiedades.

     Cuando el usuario crea una nueva instancia de la clase , este valor hace que a la propiedad de dominio se le asigne automáticamente un valor diferente. El comportamiento predeterminado agrega un número al final del nombre de clase. Esto no impide que el usuario cambie el nombre a un duplicado, pero ayuda en el caso de que el usuario no establezca el valor antes de guardar el modelo.

- Habilite la validación del DSL. En el Explorador dsl, seleccione Editor\Validación y establezca las **propiedades Uses...** en `true` .

     Hay un método de validación generado automáticamente que comprueba si hay ambigüedades. El método está en la `Load` categoría de validación. Esto asegura que se advertirá al usuario de que es posible que no sea posible volver a abrir el archivo.

     Para obtener más información, [vea Validación en un Domain-Specific lenguaje .](../modeling/validation-in-a-domain-specific-language.md)

### <a name="moniker-paths-and-qualifiers"></a>Rutas de acceso y calificadores de Moniker

Un moniker de clave calificado termina con la clave de moniker y tiene como prefijo el moniker de su elemento primario en el árbol de inserción. Por ejemplo, si el moniker de un álbum es:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

A continuación, una de las canciones de ese álbum podría ser:

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Sin embargo, si en su lugar se hace referencia a los álbumes por identificador, los monikers serían los siguientes:

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Tenga en cuenta que, dado que un GUID es único, nunca tiene como prefijo el moniker de su elemento primario.

Si sabe que una propiedad de dominio determinada siempre tendrá un valor único dentro de un modelo, puede establecer **Calificador de Moniker** is en `true` para esa propiedad. Esto hará que se use como calificador, sin usar el moniker del elemento primario. Por ejemplo, si establece Is **Moniker Qualifier** y Is **Moniker Key** para la propiedad de dominio Title de la clase Album, el nombre o identificador del modelo no se usa en monikers para Album y sus elementos secundarios incrustados:

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personalización de la estructura del XML

Para realizar las siguientes personalizaciones, expanda el nodo **Comportamiento de serialización xml** en el Explorador dsl. En una clase de dominio, expanda el nodo Datos de elemento para ver la lista de propiedades y relaciones que tienen como origen esta clase. Seleccione una relación y ajuste sus opciones en el ventana Propiedades.

- Establezca **Omitir elemento en** true para omitir el nodo de rol de origen y dejar solo la lista de elementos de destino. No debe establecer esta opción si hay más de una relación entre las clases de origen y de destino.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Establezca **Usar formulario completo para** insertar los nodos de destino en nodos que representan las instancias de relación. Esta opción se establece automáticamente al agregar propiedades de dominio a una relación de dominio.

    ```xml
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

- Establezca **Elemento**  =  **Representation** para que tenga una propiedad de dominio guardada como un elemento en lugar de como un valor de atributo.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Para cambiar el orden en el que se serializan los atributos y las  relaciones,  haga clic con el botón derecho en un elemento en Datos de elemento y use los comandos de menú Subir o Bajar.

## <a name="major-customization-using-program-code"></a>Personalización principal mediante código de programa

Puede reemplazar partes o todos los algoritmos de serialización.

Se recomienda estudiar el código en **Dsl\Generated Code\Serializer.cs** y **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Para personalizar la serialización de una clase determinada

1. Set **Is Custom en** el nodo de esa clase en Comportamiento de **serialización XML.**

2. Transformar todas las plantillas, compilar la solución e investigar los errores de compilación resultantes. Los comentarios cercanos a cada error explican qué código debe proporcionar.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Para proporcionar su propia serialización para todo el modelo

1. Invalidar métodos en Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Opciones del comportamiento de serialización xml

En el Explorador DSL, el nodo Comportamiento de serialización Xml contiene un nodo secundario para cada clase de dominio, relación, forma, conector y clase de diagrama. En cada uno de esos nodos hay una lista de propiedades y relaciones con origen en ese elemento. Las relaciones se representan por sí solas y bajo sus clases de origen.

En la tabla siguiente se resumen las opciones que puede establecer en esta sección de la definición de DSL. En cada caso, seleccione un elemento en dsl explorer y establezca las opciones en el ventana Propiedades.

### <a name="xml-class-data"></a>Datos de clase Xml

Estos elementos se encuentran en el Explorador dsl en **Comportamiento de serialización xml\Datos de clase**.

|Propiedad|Descripción|
|-|-|
|Tiene un esquema de elemento personalizado|Si es True, indica que la clase de dominio tiene un esquema de elemento personalizado.|
|Es personalizado|Establezca esta opción **en True** si desea escribir su propio código de serialización y deserialización para esta clase de dominio.<br /><br /> Compile la solución e investigue los errores para detectar instrucciones detalladas.|
|Clase de dominio|Clase de dominio a la que se aplica este nodo de datos de clase. Solo lectura.|
|Nombre del elemento|Nombre de nodo Xml para los elementos de esta clase. El valor predeterminado es una versión en minúsculas del nombre de clase de dominio.|
|Nombre del atributo Moniker|Nombre del atributo utilizado en los elementos moniker para contener la referencia. Si está en blanco, se usa el nombre de la propiedad de clave o el identificador.<br /><br /> En este ejemplo, es "name":  `<personMoniker name="/Mike Nash"/>`|
|Nombre del elemento Moniker|Nombre del elemento xml utilizado para monikers que hacen referencia a elementos de esta clase.<br /><br /> El valor predeterminado es una versión en minúscula del nombre de clase con el sufijo "Moniker". Por ejemplo, `personMoniker`.|
|Nombre del tipo de moniker|Nombre del tipo XSD generado para los monikers para los elementos de esta clase. Xsd está en **Dsl\Generated Code \\ \* Schema.xsd**|
|Id. de serialización|Si es True, el GUID del elemento se incluye en el archivo. Esto debe ser true si no hay ninguna propiedad marcada como **Is Moniker Key** y el DSL define las relaciones de referencia a esta clase.|
|Nombre del tipo|Nombre del tipo XML generado en el XSD de la clase de dominio designada.|
|Notas|Notas informales asociadas a este elemento|

### <a name="xml-property-data"></a>Datos de propiedad Xml

Los nodos de propiedad Xml se encuentran en los nodos de clase.

|Propiedad|Descripción|
|-|-|
|Propiedad domain|Propiedad a la que los datos de configuración de serialización de XML se aplican. Solo lectura.|
|Es clave de moniker|Si es True, la propiedad se usa como clave para crear monikers que hacen referencia a instancias de esta clase de dominio.|
|Calificador de Moniker|Si es True, la propiedad se usa para crear el calificador en monikers. Si es false, y si SerializeId no es true para esta clase de dominio, los monikers se califican mediante el moniker del elemento primario del árbol de inserción.|
|Representación|Si es un atributo, la propiedad se serializará como un atributo XML; si es un elemento, se serializa como elemento; si se omite, no se serializará.|
|Nombre xml|Nombre utilizado para el atributo o elemento XML que representa la propiedad. De forma predeterminada, se trata de una versión en minúsculas del nombre de propiedad de dominio.|
|Notas|Notas informales asociadas a este elemento|

### <a name="xml-role-data"></a>Datos de rol Xml

Los nodos de datos de rol se encuentran en los nodos de clase de origen.

|Propiedad|Descripción|
|-|-|
|Tiene Moniker personalizado|Establezca esta opción en true si desea proporcionar su propio código para generar y resolver monikers que atraviesan esta relación.<br /><br /> Para obtener instrucciones detalladas, compile la solución y, a continuación, haga doble clic en los mensajes de error.|
|Relación de dominio|Especifica la relación a la que se aplican estas opciones. Solo lectura.|
|Elemento Omit|Si es true, el nodo XML que corresponde al rol de origen se omite del esquema.<br /><br /> Si hay más de una relación entre las clases de origen y de destino, este nodo de rol distingue entre los vínculos que pertenecen a las dos relaciones. Por lo tanto, se recomienda no establecer esta opción en este caso.|
|Nombre del elemento Role|Especifica el nombre del elemento XML que se deriva del rol de origen. El valor predeterminado es el nombre de propiedad del rol.|
|Usar formulario completo|Si es true, cada elemento de destino o moniker se incluye en un nodo XML que representa la relación. Debe establecerse en true si la relación tiene sus propias propiedades de dominio.|

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)
