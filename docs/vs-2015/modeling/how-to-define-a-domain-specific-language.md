---
title: How to Define a Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4bcd1f1f023c9e439fb870c9e31f07aa5be215d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299547"
---
# <a name="how-to-define-a-domain-specific-language"></a>Cómo: Definir lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para definir un lenguaje específico del dominio (DSL), se crea una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a partir de una plantilla. La parte clave de la solución es el diagrama DSL Definition (Definición de DSL), que se almacena en DslDefinition.dsl. DSL Definition (Definición de DSL) define las clases y las formas del DSL. Después de modificar y agregar estos elementos, puede agregar código de programa para personalizar el DSL con más detalle.

 If you are new to DSLs, we recommend that you work through the **DSL Tools Lab**, which you can find in this site: [Visualizaton and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Selecting a Template Solution
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 Para crear un nuevo lenguaje específico del dominio, cree una nueva solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando la plantilla de proyecto Domain-Specific Language (Lenguaje específico del dominio).

#### <a name="to-create-a-dsl-solution"></a>Para crear una solución de DSL

1. Create a solution with the **Domain-Specific Language** template, which can be found under **Other Project Types/Extensibility** in the **New Project** dialog box.

    ![Create DSL dialog](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    When you click **OK**, the **Domain-Specific Language Wizard** opens and displays a list of template DSL solutions.

2. Haga clic en cada plantilla para ver una descripción. Elija la solución que más se parezca a lo que quiere crear.

    Cada plantilla DSL define un DSL de trabajo básico. Editará este DSL para que se ajuste a sus requisitos.

    Haga clic en cada muestra para obtener más información.

   - Select **Task Flow** to create a DSL that has swimlanes. Las calles son particiones verticales u horizontales del diagrama.

   - Select **Component Models** to create a DSL that has ports. Los puertos son pequeñas formas en el borde de una forma mayor.

   - Select **Class Diagrams** to define a DSL that has compartment shapes. Las formas de compartimiento contienen listas de elementos.

   - Select **Minimal Language** in other cases, or if you are uncertain.

       > [!NOTE]
       > Si quiere crear un diagrama de clases o un diagrama de componentes, considere la posibilidad de usar modelos UML. Las herramientas de modelado UML proporcionan un conjunto de diagramas que se integran alrededor de un único modelo. Son extensibles y se pueden integrar con su DSL mediante ModelBus. For more information, see [Create models for your app](../modeling/create-models-for-your-app.md).

   - Select **Minimal WinForm Designer** or **Minimal WPF Designer** to create a DSL that is displayed on a Windows Forms or WPF surface. Tendrá que escribir código para definir el editor. Para obtener más información, vea los temas siguientes:

        [Crear lenguajes específicos de dominio basados en Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Crear lenguajes específicos de dominio basados en WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Escriba una extensión de nombre de archivo para su DSL en la página del asistente correspondiente. Esta es la extensión que usarán los archivos que contienen instancias de su DSL.

   - Elija una extensión de nombre de archivo que no esté asociada con ninguna aplicación en su equipo o en algún equipo donde quiera instalar el DSL. For example, **docx** and **htm** would be unacceptable file name extensions.

   - El asistente le advertirá en caso de que la extensión que haya especificado se esté usando como un DSL. Piense en usar una extensión de nombre de archivo diferente. También puede restablecer la instancia de Visual Studio SDK Experimental para borrar antiguos diseñadores experimentales. Click **Start**, click **All Programs**, **Microsoft Visual Studio 2010 SDK**, **Tools**, and then **Reset the Microsoft Visual Studio 2010 Experimental instance**.

4. Puede ajustar la configuración en las demás páginas o dejar los valores predeterminados.

5. Haga clic en **Finalizar**.

    El asistente crea una solución que contiene dos o tres proyectos, y genera código a partir de la definición de DSL.

   Ahora, la interfaz de usuario es similar a la imagen siguiente.

   ![diseñador dsl](../modeling/media/dsl-designer.png "dsl_designer")

   Esta solución define un lenguaje específico de dominio. For more information, see [Overview of the Domain-Specific Language Tools User Interface](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Probar la solución
 La solución de plantilla proporciona un DSL de trabajo, que puede modificar o usar tal cual.

 Para probar la solución, presione F5 o CTRL+F5. Se abre una nueva instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en modo experimental.

 En la nueva instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], en el Explorador de soluciones, abra el archivo Sample. Se abre como un diagrama, con un cuadro de herramientas.

 If you run a solution that you have created from the **Minimal Language** template, your experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] will resemble the following example:

 ![](../modeling/media/dsl-min.png "DSL_min")

 Experimente con las herramientas. Cree elementos y conéctelos.

 Cierre la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

> [!NOTE]
> Cuando haya modificado el DSL, ya no podrá ver las formas en el archivo de prueba Sample. Sin embargo, podrá crear nuevos elementos.

### <a name="modifying-the-template-dsl"></a>Modificar la plantilla de DSL
 Cambie el nombre y conserve algunas o todas las clases de dominio y clases de forma en la plantilla de definición de DSL. Los nuevos nombres de clase deben ser nombres CLR válidos, sin espacios ni puntuación.

 Conservar estas clases es especialmente útil:

- The root class appears at the upper-left of the DSL Definition diagram, under **Classes and Relationships**. Asígnele otro nombre según el DSL. For example, a DSL named **MusicLibrary** might have a root class named **Music**.

- The diagram class appears at the lower right of the DSL Definition diagram, in the **Diagram Elements** column. Quizás tenga que desplazarse a la derecha para verlo. It is typically named _YourDsl_**Diagram**.

- If you used the **Task Flow** template and you want to create diagrams with swimlanes, keep and rename the Actor domain class and ActorSwimlane shape.

  Elimine o cambie el nombre de otras clases para que se ajusten a sus necesidades.

## <a name="patterns"></a> Patterns for Defining a DSL
 Le recomendamos que desarrolle un DSL agregando o ajustando una o dos características cada vez. Agregue una característica, ejecute el DSL y pruébelo y, después, agregue una o dos características más. Una característica típica de su DSL podría ser:

- Una clase de dominio, la relación de incrustación que conecta el elemento con el modelo, la forma necesaria para mostrar elementos de esa clase en el diagrama y la herramienta de elemento que permite a los usuarios crear elementos.

- Las propiedades de dominio de una clase de dominio y los elementos Decorator que los muestran en una forma.

- Una relación de referencia y el conector que la muestra en el diagrama, y la herramienta de conector que permite a los usuarios crear vínculos.

- Una personalización que requiere código de programa, como una restricción de validación o un comando de menú.

  En las secciones siguientes se describe cómo construir los tipos de características DSL más útiles. Hay muchos otros patrones con los que se puede construir un DSL, pero estos son los que se usan con más frecuencia.

> [!NOTE]
> After adding a feature, do not forget to click **Transform All Templates** in the toolbar of Solution Explorer before you build and running your DSL.

 La figura siguiente muestra las clases y relaciones que forman parte del DSL y que se usan como ejemplo en este tema.

 ![Embedding and Reference relationships](../modeling/media/music-classes.png "Music_Classes")

 La siguiente figura es un modelo de ejemplo de este DSL:

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> Con "modelo" nos referimos a una instancia de su DSL que los usuarios crean y que normalmente se muestra como un diagrama. En este tema se explican tanto el diagrama DSL Definition (Definición de DSL) como los diagramas de modelo que aparecen cuando se usa su DSL.

## <a name="classes"></a> Defining Domain Classes
 Las clases de dominio representan los conceptos de su DSL. The instances are *model elements*. For example in a **MusicLibrary** DSL you might have Domain Classes named **Album** and **Song**.

 To create a domain class, you can drag from the **Named Domain Class** tool to the diagram, and then rename the class.

 For more information, see [Properties of Domain Classes](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Crear una relación incrustada para cada clase de dominio
 Todas las clases de dominio, excepto la clase raíz, deben ser el destino de al menos una relación de incrustación, o deben heredar de una clase que sea el destino de una relación de incrustación.

 En un modelo, todos los elementos de modelo son nodos de un único árbol de relaciones incrustadas. El origen y el destino de una relación de incrustación suelen denominarse clases primaria y secundaria.

 La selección de una clase primaria para una clase de dominio depende de cómo quiere que la duración de sus elementos dependa de otros elementos. Si se elimina un nodo de un árbol, normalmente también se elimina su subárbol. Por lo tanto, las clases de elemento que tienen una existencia independiente se incrustan directamente debajo de la clase raíz.

 Normalmente, si muestra un elemento dentro de otro elemento, quiere indicar una relación de propiedad. En ese caso, la clase primaria más apropiada es la clase del contenedor. La excepción es cuando el elemento que ve dentro del contendor es tan solo un vínculo de referencia a un elemento independiente. En ese caso, al eliminar el contenedor se elimina la referencia pero no el destino.

 En los patrones de una definición de DSL que se describen en este tema, damos por hecho que los elementos que se muestran dentro de un contenedor se eliminarán cuando el contenedor se elimine. Se pueden lograr esquemas más complejos mediante la definición de reglas.

|Cómo se muestra el elemento|Clase primaria (incrustación)|Ejemplo en la plantilla de solución de DSL|
|------------------------------|--------------------------------|--------------------------------------|
|Forma en el diagrama<br /><br /> Calle.|Clase raíz del DSL.|Minimal Language.<br /><br /> Task Flow: Actor class.|
|Forma en una calle.|Clase de dominio de los elementos que se muestran como calles.|Task Flow: Task class.|
|Elemento en una lista en una forma; el elemento se elimina si el contenedor se elimina.<br /><br /> Puerto en el borde de una forma.|Clase de dominio que se asigna a la forma del contenedor.|Class diagram: Attribute class.<br /><br /> Component diagram: Port class.|
|Elemento en una lista; no se elimina si el contenedor se elimina.|Clase raíz del DSL.<br /><br /> La lista muestra vínculos de referencia.||
|No se muestra directamente.|Clase de la que forma parte.||

 En el ejemplo de la biblioteca de música, los álbumes se muestran como rectángulos en los que se enumeran los títulos de las canciones. Por lo tanto, la clase primaria de Album es la clase raíz Music, y la clase primaria de Song es Album.

 To create a domain class and its embedding at the same time, click the **Embedding Relationship** tool, then click the parent class, and then click on a blank part of the diagram.

 Normalmente no es necesario ajustar el nombre de la relación de incrustación y de sus roles, porque rastrearán los nombres de las clases automáticamente.

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Incrustación no es lo mismo que herencia. En una relación de incrustación, las clases secundarias no heredan las características de sus primarias.

### <a name="add-domain-properties-to-each-domain-class"></a>Agregar propiedades de dominio a cada clase de dominio
 Las propiedades de dominio almacenan valores. Examples are: Name, Title, Publication Date.

 Click **Domain Properties** in the class, press the ENTER key, and then type the name of a property. El tipo predeterminado de una propiedad de dominio es String. If you want to change the type, select the domain property, and set the **Type** in the **Properties** window. If the type that you want is not in the drop-down list, see [Adding Property Types](#addTypes).

 **Set an Element Name property.** Select a domain property that can be used to identify elements in the language explorer. Por ejemplo, en la clase de dominio Song que pueda seleccionar la propiedad de dominio Title (Título). In the **Properties** window, set **Is Element Name** to `true`.

### <a name="create-derived-domain-classes"></a>Crear clases de dominio derivadas
 Si quiere que una clase de dominio tenga variantes que hereden sus propiedades y relaciones, cree clases que deriven de ella. Por ejemplo, Album podría tener las clases derivadas WMA y MP3.

 Create the derived class using the **Domain Class** tool.

 Click the **Inheritance** tool, click the derived class, and then click the base class.

 Consider setting the **Inheritance Modifier** of the base class to **abstract**. Si cree que puede necesitar instancias de la clase base, considere la posibilidad de crear en su lugar una clase derivada diferente para ellas.

 Las clases derivadas heredan las propiedades y los roles de sus clases base.

### <a name="tidy-the-dsl-definition-diagram"></a>Ordenar el diagrama DSL Definition (Definición de DSL)
 Cuando se agregan relaciones, algunas de las clases aparecen en más de un lugar. To reduce the number of appearances and make the diagram wider, right-click the target class of a relationship, and then click **Bring Tree Here**. For the opposite effect, right-click the target class of a relationship and click **Split Tree**. Si no ve estos comandos del menú, asegúrese de que solo está seleccionada la clase de dominio.

 Use CTRL+Flecha arriba y CTRL+Flecha abajo para mover las clases de dominio y las clases de forma.

### <a name="test-the-domain-classes"></a>Probar las clases de dominio

##### <a name="to-test-the-new-domain-classes"></a>Para probar las nuevas clases de dominio

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code. Este paso se puede automatizar. For more information, see [How to Automate Transform All Templates](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un archivo que tenga la extensión de nombre de archivo de su DSL.

3. **Open the Explorer.** At the side of the diagram is the language explorer window, which is usually named *YourLanguage* Explorer. Si no ve esta ventana, podría estar en una pestaña debajo del Explorador de soluciones. If you cannot find it, on the **View** menu, point to **Other Windows**, and then click _YourLanguage_**Explorer**.

     El explorador presenta una vista de árbol del modelo.

4. **Create new elements.** Right-click the root node at the top, and then click **Add New**_YourClass_.

     En el explorador del lenguaje aparece una nueva instancia de su clase.

5. Cuando cree nuevas instancias, compruebe que cada instancia tenga un nombre diferente. This will occur only if you have set the **Is Element Name** flag on a domain property.

6. **Examine the domain properties. With an instance of your class selected,** inspect the Properties window. Debe mostrar las propiedades de dominio que ha definido en esta clase de dominio.

7. **Save the file, close it, and re-open it**. Después de expandir los nodos en el explorador, todas las instancias creadas deben ser visibles.

## <a name="shapes"></a> Defining Shapes on the Diagram
 Puede definir clases de elementos que aparecen en un diagrama, como rectángulos, elipses o iconos.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Para definir una clase de elementos que aparecen como formas en un diagrama

1. **Define and test a domain class as described in**  [Defining Domain Classes](#classes) **.**

   - La clase primaria debería ser la clase raíz. Es decir, debería haber una relación de incrustación entre la clase raíz y la nueva clase de dominio.

   - Si el diagrama tiene calles, la clase primaria puede ser la clase de dominio que está asignada a una calle. Before continuing with this procedure, see [Defining a DSL that has Swimlanes](#swimlanes).

2. **Add a shape class** to represent the elements on the model diagram. Arrastre desde una de las siguientes herramientas al diagrama DSL Definition (Definición de DSL):

   - **Geometry Shape** provides a rectangle or ellipse.

   - **Image Shape** displays an image that you provide.

   - **Compartment Shape** is a rectangle that contains one or more lists of items.

     Cambie el nombre de la clase de forma, que aparecerá en el lado derecho del diagrama DSL Definition (Definición de DSL), en Shapes and Connectors (Formas y conectores).

3. **Define an image, if you created an image shape**.

   1. Cree un archivo de imagen de cualquier tamaño. Se admiten los formatos BMP, JPEG, GIF y EMF.

   2. En el Explorador de soluciones, agregue el archivo a la solución, en Dsl\Resources.

   3. Vuelva al diagrama DSL Definition (Definición de DSL) y seleccione la nueva clase de forma de imagen.

   4. In the Properties window, click the **Image** property.

   5. In the **Select Image** dialog box, click the drop-down menu under **File name**, and select the image.

4. **Add text decorators to the shape, to display the domain properties.**

    Para mostrar el nombre o el título del elemento de modelo, probablemente necesitará al menos un elemento Decorator de texto.

    Right-click the header of the shape class, point to **Add**, and then click **Text Decorator**. Set the name of the decorator, and in the Properties window set its **Position**.

5. **Connect each shape with a Diagram Element Map to the domain class that it should display**.

    Click the **Diagram Element Map** tool, then click the domain class, then click the shape class.

6. **Map the properties to the text decorators.**

   1. Seleccione la línea gris entre la clase de dominio y la clase de forma que representa la asignación de elemento de diagrama.

   2. In the **DSL Details** window, click the **Decorator Maps** tab. If you do not see the **DSL Details** window, on the **View** menu, point to **Other Windows** and then click **DSL Details**. Normalmente es necesario levantar la parte superior de esta ventana para ver todo su contenido.

   3. Seleccione el nombre de un elemento Decorator. Under **Display property**, select the name of a property of the domain class. Repita este paso para cada elemento Decorator.

       If you want to display a property of a related element, click the drop-down tree navigator under **Path to display property**.

   4. Asegúrese de que hay una marca de verificación junto al nombre de cada elemento Decorator.

      ![Shape Mappings and DSL Details window](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Make a toolbox item for creating elements of the domain class.**

   1. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

   2. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

       > [!NOTE]
       > If you right-click the **Tools** node, you will not see **Add Element Tool**. En su lugar, haga clic en el nodo situado encima de él.

   3. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

   4. Set **Caption** and **Tooltip**.

   5. Set **Toolbox Icon** to an icon that will appear in the toolbox. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

        To create a new icon, open Dsl\Resources in **Solution Explorer**. Copie y pegue uno de los archivos BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

        Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

   For more information, see [Properties of Geometry Shapes](../modeling/properties-of-geometry-shapes.md) and [Properties of Image Shapes](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Para probar las formas

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un archivo que tenga la extensión de nombre de archivo de su DSL.

3. **Verify that the element tools appear on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. Cuando se edita la propiedad en la ventana Properties (Propiedades) o en el elemento Decorator, la otra vista se actualiza.

   Después de probar una forma por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Defining Reference Relationships
 Puede definir una relación de referencia entre cualquier clase de dominio de origen y cualquier clase de dominio de destino. Las relaciones de referencia suelen mostrarse en un diagrama como conectores, que son líneas entre formas.

 Por ejemplo, si los álbumes y los artistas se muestran como formas en el diagrama, podría definir una relación llamada ArtistsAppearedOnAlbums que vincula los artistas con los álbumes en los que han trabajado. Vea el ejemplo en la figura.

 ![Instance model of generated DSL](../modeling/media/music-instance.png "Music_Instance")

 Las relaciones de referencia también pueden vincular elementos del mismo tipo. Por ejemplo, en un DSL que representa un árbol genealógico, la relación entre los padres y los hijos es una relación de referencia de persona a persona.

### <a name="define-a-reference-relationship"></a>Definir una relación de referencia
 Haga clic en la herramienta Reference Relationship (Relación de referencia), haga clic en la clase de dominio de origen de la relación y, después, haga clic en la clase de dominio de destino. La clase de destino puede ser la misma que la clase de origen.

 Cada relación tiene dos roles, representados por la línea a cada lado del cuadro de relación. Puede seleccionar cada rol y establecer sus propiedades en la ventana Properties (Propiedades).

 **Consider renaming the roles**. Por ejemplo, en una relación entre personas, quizás quiera cambiar los nombres predeterminados por Padres e Hijos, Director y Subordinados, Profesor y Estudiante, etc.

 **Adjust the multiplicities of each role**, if it is necessary. Si quiere que cada persona tenga al menos un director, establezca la multiplicidad que aparece debajo de la etiqueta Director en el diagrama a 0..1.

 **Add domain properties to the relationship.** In the figure, the Artist-Album relationship has a property of role.

 **Set the Allows Duplicates property of the relationship,** if more than one link of the same class can exist between the same pair of model elements. Por ejemplo, podría permitir que un Profesor enseñe más de una Asignatura al mismo Estudiante.

 ![Shape maps for connectors](../modeling/media/music-connector.png "Music_Connector")

 For more information, see [Properties of Domain Relationships](../modeling/properties-of-domain-relationships.md) and [Properties of Domain Roles](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definir un conector para mostrar la relación
 Un conector muestra una línea entre dos formas en el diagrama del modelo.

 Drag the **Connector** tool onto the DSL definition diagram.

 Agregue elementos Decorator de texto si quiere mostrar etiquetas en el conector. Establezca sus posiciones. To let the user move a text decorator, set its **Is Moveable** property.

 Use the **Diagram Element Map** tool to link the connector to the reference relationship.

 With the diagram element map selected, open the **DSL Details** window, and open the **Decorator Maps** tab.

 Select each **Decorator** and set **Display property** to the correct domain property.

 Make sure that a check mark appears next to each item in the **Decorators** list.

### <a name="define-a-connection-builder-tool"></a>Definir una herramienta Connection Builder (Generador de conexiones)
 In the **DSL Explorer** window, expand the **Editor** node and all its subnodes.

 Right-click the node that has the same name as your DSL, and then click **Add New Connection Tool**.

 Con la nueva herramienta seleccionada, en la ventana Properties (Propiedades):

- Set the **Caption** and **Tooltip**.

- Click **Connection Builder** and select the appropriate builder for the new relationship.

- Set **Toolbox Icon** to the icon that you want to appear in the toolbox. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Copie y pegue uno de los archivos BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your .BMP file from the drop-down menu.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Para probar una relación de referencia y un conector

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un archivo que tenga la extensión de nombre de archivo de su DSL.

3. **Verify that the connection tool appears on the toolbox.**

4. **Create shapes** by dragging from a tool onto the model diagram.

5. **Create connections** between the shapes. Haga clic en la herramienta de conector, en una forma y, después, en otra forma.

6. **Verify that you cannot create connections between inappropriate classes.** For example, if your relationship is between Albums and Artists, verify that you cannot link Artists to Artists.

7. **Verify that the multiplicities are correct. For example, verify that you cannot connect a Person to more than one manager.**

8. **Verify that each text decorator appears,** and that:

   1. You can edit it, unless you have set the **Is UI Read Only** flag on the domain property.

   2. Cuando se edita la propiedad en la ventana Properties (Propiedades) o en el elemento Decorator, la otra vista se actualiza.

   Después de probar un conector por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Defining Shapes that Contain Lists: Compartment Shapes
 Una forma de compartimiento contiene una o varias listas de elementos. Por ejemplo, en un DSL de biblioteca de música, podría usar formas de compartimiento para representar álbumes de música. En cada álbum, hay una lista de canciones.

 ![Compartment Shape](../modeling/media/compartmentshape.png "CompartmentShape")

 En el método más sencillo de lograr este efecto en una definición de DSL, se define una clase de dominio para el contenedor y una clase de dominio para cada lista. La clase de contenedor se asigna a la forma de compartimiento.

 ![Shape map](../modeling/media/music-mapcomp.png "Music_MapComp")

 For more information, see [Properties of Compartment Shapes](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Para definir una forma de compartimiento

1. **Create the container domain class**. Click the **Embedding Relationship** tool, click the root class of the model, and then click a blank part of the DSL definition diagram. Esto crea la clase de dominio llamada Album en la figura de ejemplo.

     En lugar de incrustarlo en la clase raíz, también puede incrustar el contenedor en una clase de dominio que esté asignada a una calle.

     Add a domain property such as Name to the class, and set its **Is Element Name** flag in the Properties window.

2. **Create the list item domain class**. Click the **Embedding Relationship** tool, click the container class (Album) and then click a blank part of the diagram. Esto crea la clase de dominio llamada Song en la figura de ejemplo.

     Add a domain property such as Title to the class, and set its **Is Element Name** flag.

     Agregue otras propiedades de dominio.

     Agregue otra clase de dominio de elemento de lista para cada lista que quiera mostrar.

3. **To mix several types of item in the list**, create classes that inherit from the list class. Make the list class abstract by setting its **Inheritance Modifier**.

     Por ejemplo, si quiere que la música clásica se ordene por compositor en lugar de por artista, podría crear dos subclases de Song, ClassicalSong y NonClassicalSong.

4. **Create the compartment shape**. Drag from the **Compartment Shape** tool onto the DSL definition diagram.

     Agregue un elemento Decorator de texto y establezca su nombre.

     Agregue un compartimiento y establezca su nombre.

5. To let the user hide the list compartments, right-click the compartment shape class, point to **Add**, and then click **Expand/Collapse Decorator**. En la ventana Properties (Propiedades), establezca la posición del elemento Decorator.

6. Click the **Diagram Element Map** tool, click the container domain class, and then click the compartment shape.

7. Seleccione el vínculo de la asignación de elemento de diagrama entre la clase de dominio y la forma. In the **DSL Details** window:

    1. Click the **Decorators** tab. Click the name of the decorator and then select the appropriate item under **Display Property**. Asegúrese de que haya una marca de verificación junto al nombre del elemento Decorator.

    2. Click the **Compartment Maps** tab.

         Haga clic en el nombre del compartimiento.

         Under **Displayed elements collection path**, navigate to the list element class (Song). Haga clic en la flecha hacia abajo para usar la herramienta de navegador.

         Under **Display Property**, select the property that should be displayed in the list. En el ejemplo, es Title.

> [!NOTE]
> Use los campos Path (Ruta de acceso) del Decorator Map (Asignación de elemento Decorator) y los campos de Compartment Maps (Asignaciones de compartimientos) para crear relaciones más complejas entre las clases de dominio y la forma de compartimiento.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Para definir una herramienta para crear la forma

1. **Make a toolbox item for creating elements of the domain class.**

2. In **DSL Explorer**, expand the **Editor** node and all its sub-nodes.

3. Right-click the node under **Toolbox Tabs** that has the same name as your DSL, for example MusicLibrary. Click **Add Element Tool**.

    > [!NOTE]
    > If you right-click the **Tools** node, you will not see **Add Element Tool**. En su lugar, haga clic en el nodo situado encima de él.

4. In the Properties window with the new element tool selected, set **Class** to the domain class that you have recently added.

5. Set **Caption** and **Tooltip**.

6. Set **Toolbox Icon** to an icon that will appear in the toolbox. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

     To create a new icon, open Dsl\Resources in **Solution Explorer**. Copie y pegue uno de los archivos .BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

     Return to the DSL Definition diagram, select the tool, and in the Properties window click **[...]** in **Toolbox Icon**. In the **Select Bitmap** dialog box, select your BMP file from the drop-down menu.

#### <a name="to-test-a-compartment-shape"></a>Para probar una forma de compartimiento

1. **Click Transform All Templates** in the toolbar of Solution Explorer, to generate the DSL designer code.

2. **Build and run the DSL.** Press F5 or CTRL+F5 to run a new instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in experimental mode. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un archivo que tenga la extensión de nombre de archivo de su DSL.

3. **Verify that the tool appears on the toolbox.**

4. Arrastre la herramienta al diagrama del modelo. Se crea una forma.

    Compruebe que el nombre del elemento aparece y se establece automáticamente en un valor predeterminado.

5. Right-click the header of the new shape, and then click Add *Your List Item.* En el ejemplo, el comando es Add Song (Agregar canción).

    Compruebe que aparece un elemento en la lista y que tiene un nombre nuevo.

6. Haga clic en uno de los elementos de lista y, después, examine la ventana Properties (Propiedades). Verá las propiedades de los elementos de lista.

7. Abra el explorador del lenguaje. Compruebe que puede ver los nodos de contenedor con los nodos de elemento de lista dentro.

   ![Generated explorer of DSL](../modeling/media/music-explorer.png "Music_Explorer")

   Después de probar una forma de compartimiento por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Mostrar un vínculo de referencia en un compartimiento
 Normalmente, un elemento que se muestra en un compartimiento es un elemento secundario del elemento que está representado por la forma de compartimiento. Pero a veces querrá mostrar un elemento que está vinculado a él con una relación de referencia.

 Por ejemplo, podríamos agregar un segundo compartimiento a AlbumShape que muestra una lista de los artistas que están vinculados al álbum.

 En este caso, el compartimiento debe mostrar el vínculo en lugar del elemento referenciado. El motivo es que quiere que, cuando el usuario seleccione el elemento en el compartimiento y presione Supr, se elimine el vínculo, no el elemento referenciado.

 En cualquier caso, puede hacer que se muestre el nombre del elemento referenciado en el compartimiento.

 En el procedimiento siguiente se da por hecho que ya ha creado la clase de dominio, la relación de referencia, la forma de compartimiento y la asignación de elemento de diagrama, tal y como se describió anteriormente en esta sección.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Para mostrar un vínculo de referencia en un compartimiento

1. **Add a compartment to the compartment shape**. On the DSL Definition diagram, right-click the compartment shape class, point to **Add**, and then click **Compartment**.

2. Set **Displayed elements collection path** to navigate to the link, instead of its target element. Haga clic en el menú desplegable y use la vista de árbol para seleccionar la relación de referencia en lugar de su destino. In the example, the relationship is **ArtistAppearedOnAlbums**.

3. Set **Path to Display Property** to navigate from the link to the target element. In the example, this is **Artist**.

4. Set **Display Property** to the appropriate property of the target element, for example **Name**.

5. **Transform All Templates**, build and run the DSL, and open a test model.

6. En el diagrama del modelo, cree las clases de forma apropiadas, establezca sus nombres y cree un vínculo entre ellas. En la forma de compartimiento, deben aparecer los nombres de los elementos vinculados.

7. Seleccione el vínculo o el elemento en la forma de compartimiento. Deben desaparecer tanto el vínculo como el elemento.

## <a name="ports"></a> Defining Ports on the Boundary of another Shape
 Un puerto es una forma que está situada en los límites de otra forma.

 Los puertos se pueden usar para proporcionar un punto de conexión fijo en otra forma al cual el usuario puede dibujar conectores. En este caso, puede hacer que la forma de puerto sea transparente.

 To see an example that uses ports, select the **Component Diagram** template when you create a new DSL solution. En este ejemplo se muestran los principales aspectos para tener en cuenta al definir puertos:

- Hay una clase de dominio que representa el contenedor de los puertos, `Component`.

- Hay una clase de dominio que representa los puertos. En el ejemplo, es `ComponentPort`.

- Hay una relación de incrustación desde la clase de dominio de contendor a la clase de dominio de puerto. For more information, see [Defining Domain Classes](#classes).

- Si quiere mezclar diferentes tipos de puerto en el mismo contenedor, puede crear subclases de la clase de dominio de puerto. En el ejemplo, `InPort` y `OutPort` heredan de `ComponentPort`.

- La clase de dominio de contenedor se puede asignar a cualquier tipo de forma. En el ejemplo, es `ComponentShape`. For more information, see [Defining Shapes](#shapes).

- Las clases de dominio de puerto se asignan a formas de puerto. Puede asignar las clases derivadas a clases de forma de puerto diferentes, o asignar la clase base a una clase de forma de puerto.

  In other respects, port shapes behave as described in [Defining Shapes](#shapes).

  For more information, see [Properties of Port Shapes](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Defining a DSL that has Swimlanes
 Las calles son una partición horizontal o vertical de un diagrama. Cada calle corresponde a un elemento de modelo. Su definición de DSL requiere una clase de dominio para los elementos de calle.

 La mejor manera de crear un DSL con calles es crear una nueva solución de DSL y elegir la plantilla de solución Task Flow (Flujo de tareas). En la definición de DSL, la clase Actor es la clase de dominio asignada a la calle. Cambie el nombre de esta y otras clases para adaptarlas a su proyecto.

 Para agregar una clase que se mostrará como una forma dentro de una calle, cree una relación de incrustación entre la clase de calle y la nueva clase. Los usuarios podrán arrastrar elementos desde una calle a otra, pero cada elemento siempre estará dentro de una calle determinada. En la plantilla de solución Task Flow (Flujo de tareas), FlowElement es una clase secundaria de la clase de calle.

 Para agregar una clase que se mostrará como una forma independiente de las calles, cree una relación de incrustación entre la clase raíz y la nueva clase. Los usuarios podrán colocar estas formas en cualquier lugar del diagrama, incluso traspasando los límites de las calles y fuera de ellas. En la plantilla de solución Task Flow (Flujo de tareas), Comment es una clase secundaria de la clase raíz.

 For more information, see [Properties of Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Adding Property Types

### <a name="domain-enumerations-and-literals"></a>Literales y enumeradores de dominio
 Una enumeración de dominio es un tipo con varios valores literales.

 To add a domain enumeration, right-click the root of the model in the **DSL Explorer** and then click **Add New Domain Enumeration**. The element will appear in the **DSL Explorer** under the **Domain Types** node. Este elemento no aparece en el diagrama.

 To add enumeration literals to the domain enumeration, right-click the domain enumeration in the **DSL Explorer** and then click **Add New Enumeration Literal**.

 De forma predeterminada, una propiedad que tiene un tipo de enumeración solo se puede establecer en un valor de la enumeración al mismo tiempo. If you want users and programmers to be able to set any combination of values - a "bit field" - set the **IsFlags** property of the Enumeration.

### <a name="external-types"></a>Tipos externos
 When you set the type of a domain property, if you do not find the type you want in the **Type** drop-down list, you can add an external type. For example, you could add the **System.Drawing.Color** type to the list.

 To add a type, right-click the root of the model in DSL Explorer, and then click **Add New External Type**. In the Properties window, set the name to **Color** and the namespace to **System.Drawing**. This type now appears in DSL Explorer under **Domain Types**. Puede elegirlo siempre que establezca el tipo de una propiedad de dominio.

## <a name="custom"></a> Customizing the DSL
 Con las técnicas descritas en este tema, puede crear rápidamente un DSL con una notación en forma de diagrama, un formato XML legible, y las herramientas básicas que se necesitan para generar código y otros artefactos.

 Hay dos métodos para extender la definición de DSL:

1. Ajuste el DSL usando más características de la definición de DSL. Por ejemplo, puede crear una sola herramienta de conector que pueda crear varios tipos de conector, y puede controlar las reglas por las que al eliminar un elemento también se eliminan los elementos relacionados. Estas técnicas se logran principalmente estableciendo valores en la definición de DSL, y algunas requieren unas cuantas líneas de código de programa.

     For more information, see [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Amplíe sus herramientas de modelado usando código de programa para lograr efectos más avanzados. Por ejemplo, puede crear comandos de menú que pueden cambiar el modelo, y puede crear herramientas que integren dos o más DSL. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL.  For more information, see [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Cambiar la definición de DSL
 Cuando se crea un elemento en una definición de DSL, muchos valores predeterminados se establecen automáticamente. Una vez establecidos, puede cambiarlos. Esto simplifica el desarrollo de un DSL, al tiempo que permite realizar personalizaciones eficaces.

 Por ejemplo, cuando se asigna una forma a un elemento, la ruta del elemento primario de la asignación se establece automáticamente de acuerdo con la relación de incrustación de la clase de dominio. Sin embargo, si más adelante cambia la relación de incrustación, la ruta del elemento primario no cambia automáticamente.

 Por lo tanto, debe tener en cuenta que, cuando se cambian algunas relaciones en una definición de DSL, no es extraño que aparezcan errores al guardar la definición o al transformar todas las plantillas. La mayoría de estos errores son fáciles de corregir. Haga doble clic en el informe de error para ver la ubicación del error.

 See also [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Troubleshooting
 En la tabla siguiente se enumeran algunos de los problemas más comunes que se encuentran al diseñar un DSL, además de sugerencias para solucionarlos. More advice is available on the [Visualization Tools Extensibililty Forum](https://go.microsoft.com/fwlink/?LinkId=186074).

|Problema|Sugerencia|
|-------------|----------------|
|Los cambios que he hecho en el archivo de definición de DSL no surten efecto.|Click **Transform All Templates** in the toolbar above Solution Explorer, and then rebuild the solution.|
|Las formas muestran el nombre de un elemento Decorator en lugar del valor de la propiedad.|Configure la asignación del elemento Decorator. En el diagrama DSL Definition (Definición de DSL), haga clic en la asignación de elemento de diagrama, que es la línea gris entre la clase de dominio y la clase de forma.<br /><br /> Open the **DSL Details** window. If you cannot see it, on the View menu, point to **Other Windows**, and then click **DSL Details**.<br /><br /> Click the **Decorator Maps** tab. Select the name of the decorator. Asegúrese de que la casilla situada junto a él está activada. Under **Display property**, select the name of a domain property.<br /><br /> For more information, see [Shapes on the Diagram](#shapes).|
|En DSL Explorer (Explorador de DSL), no puedo agregar nada a una colección. Por ejemplo, al hacer clic con el botón secundario en Tools (Herramientas), no hay ningún comando "Add Tool" (Agregar herramienta) en el menú.<br /><br /> En el explorador de mi DSL, no puedo agregar un elemento a una lista.|Haga clic en el elemento situado encima del nodo que está intentando. Cuando quiera agregar algo a una lista, el comando Add (Agregar) no está en el nodo de lista, sino en su propietario.|
|Creé una clase de dominio pero no puedo crear instancias en el explorador del lenguaje.|Todas las clases de dominio, excepto la raíz, deben ser el destino de una relación de incrustación.|
|En el explorador de mi DSL, los elementos se muestran solo con sus nombres de tipo.|In the DSL Definition, select a domain property of the class and in the Properties window, set **Is Element Name** to true.|
|Mi DSL siempre se abre en el editor XML.|El motivo puede ser que se produjo un error mientras se leía el archivo. Sin embargo, después de corregir ese error, debe restablecer explícitamente el editor para que sea su diseñador de DSL.<br /><br /> Right-click the project item, click **Open With** and select _YourLanguage_**Designer (Default)** .|
|El cuadro de herramientas de mi DSL no aparece después de cambiar los nombres de ensamblado.|Inspect and update **DslPackage\GeneratedCode\Package.tt** For more information, see [How to: Change the Namespace of a Domain-Specific Language](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|El cuadro de herramientas de mi DSL no aparece, pero no he cambiado el nombre del ensamblado.<br /><br /> O bien, se muestra un cuadro de mensaje que indica un error al cargar una extensión.|Restablezca la instancia experimental y vuelva a compilar la solución.<br /><br /> 1.  At the Windows Start menu, under **All Programs**, expand [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)], then **Tools**, and then click **Reset the Microsoft Visual Studio Experimental Instance**.<br />2.  On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**.|

## <a name="see-also"></a>Vea también
 [Getting Started with Domain-Specific Languages](../modeling/getting-started-with-domain-specific-languages.md) [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md)
