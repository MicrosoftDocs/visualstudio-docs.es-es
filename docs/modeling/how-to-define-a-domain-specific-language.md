---
title: 'Cómo: Definir lenguajes específicos de dominio'
description: Obtenga información sobre cómo crear una Visual Studio a partir de una plantilla para definir un lenguaje específico de dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51717e4bdbf12478e22bb825a9c84cfc82815f98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387364"
---
# <a name="how-to-define-a-domain-specific-language"></a>Cómo: Definir lenguajes específicos de dominio
Para definir un lenguaje específico de dominio (DSL), cree una solución Visual Studio a partir de una plantilla. La parte clave de la solución es el diagrama DSL Definition (Definición de DSL), que se almacena en DslDefinition.dsl. DSL Definition (Definición de DSL) define las clases y las formas del DSL. Después de modificar y agregar estos elementos, puede agregar código de programa para personalizar el DSL con más detalle.

Si no está seguro de las DSL, le recomendamos que trabaje en el laboratorio de herramientas de **DSL,** que puede encontrar en este sitio: SDK de visualización [y modelado.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Selección de una solución de plantilla

Para definir un DSL, debe tener instalados los siguientes componentes:

- Programa para la mejora
- Visual Studio de trabajo de desarrollo de extensiones (incluye el SDK Visual Studio)
- SDK de modelado (instalarlo como un componente individual en Visual Studio)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Para crear un nuevo lenguaje específico del dominio, cree una nueva solución Visual Studio mediante la plantilla de proyecto Domain-Specific Language.

### <a name="to-create-a-dsl-solution"></a>Para crear una solución de DSL

1. Cree un nuevo **proyecto de lenguaje específico de** dominio.

   ::: moniker range="vs-2017"

    ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

   ::: moniker-end

    Se **abre el Asistente para lenguaje específico del** dominio y se muestra una lista de soluciones DSL de plantilla.

2. Haga clic en cada plantilla para ver una descripción. Elija la solución que más se parezca a lo que quiere crear.

    Cada plantilla DSL define un DSL de trabajo básico. Editará este DSL para que se ajuste a sus requisitos.

    Haga clic en cada muestra para obtener más información.

   - Seleccione **Flujo de tareas** para crear un DSL que tenga calles. Las calles son particiones verticales u horizontales del diagrama.

   - Seleccione **Modelos de componentes** para crear un DSL que tenga puertos. Los puertos son pequeñas formas en el borde de una forma mayor.

   - Seleccione **Diagramas de clases** para definir un DSL que tenga formas de compartimiento. Las formas de compartimiento contienen listas de elementos.

   - Seleccione **Lenguaje mínimo** en otros casos o si no está seguro.

   - Seleccione **Diseñador mínimo de WinForm o** Diseñador **WPF** mínimo para crear un DSL que se muestra en una Windows Forms o WPF. Tendrá que escribir código para definir el editor. Para obtener más información, vea los temas siguientes:

        [Crear lenguajes específicos de dominio basados en Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Crear lenguajes específicos de dominio basados en WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Escriba una extensión de nombre de archivo para su DSL en la página del asistente correspondiente. Esta es la extensión que usarán los archivos que contienen instancias de su DSL.

   - Elija una extensión de nombre de archivo que no esté asociada con ninguna aplicación en su equipo o en algún equipo donde quiera instalar el DSL. Por ejemplo, **docx** y **htm** serían extensiones de nombre de archivo inaceptables.

   - El asistente le advertirá en caso de que la extensión que haya especificado se esté usando como un DSL. Piense en usar una extensión de nombre de archivo diferente. También puede restablecer la instancia de Visual Studio SDK Experimental para borrar antiguos diseñadores experimentales. Haga **clic en** Inicio , en **Todos** los **programas, Microsoft Visual Studio SDK de 2010,** Herramientas **y,** a continuación, en Restablecer la instancia experimental de **Microsoft Visual Studio 2010**.

4. Puede ajustar la configuración en las demás páginas o dejar los valores predeterminados.

5. Haga clic en **Finalizar**

    El asistente crea una solución que contiene dos o tres proyectos, y genera código a partir de la definición de DSL.

   Ahora, la interfaz de usuario es similar a la imagen siguiente.

   ![diseñador dsl](../modeling/media/dsl_designer.png)

   Esta solución define un lenguaje específico de dominio. Para obtener más información, vea [Información general de Domain-Specific Language Tools Interfaz de usuario](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Probar la solución
 La solución de plantilla proporciona un DSL de trabajo, que puede modificar o usar tal cual.

 Para probar la solución, presione F5 o CTRL+F5. Se abre una nueva instancia Visual Studio en modo experimental.

 En la nueva instancia de Visual Studio, en Explorador de soluciones, abra el archivo de ejemplo. Se abre como un diagrama, con un cuadro de herramientas.

 Si ejecuta una solución que ha creado a partir de la plantilla **Lenguaje** mínimo, el Visual Studio experimental será similar al ejemplo siguiente:

 ![Árbol de ejemplo de lenguaje específico del dominio en Visual Studio](../modeling/media/dsl_min.png)

 Experimente con las herramientas. Cree elementos y conéctelos.

 Cierre la instancia experimental de Visual Studio.

> [!NOTE]
> Cuando haya modificado el DSL, ya no podrá ver las formas en el archivo de prueba Sample. Sin embargo, podrá crear nuevos elementos.

### <a name="modifying-the-template-dsl"></a>Modificar la plantilla de DSL
 Cambie el nombre y conserve algunas o todas las clases de dominio y clases de forma en la plantilla de definición de DSL. Los nuevos nombres de clase deben ser nombres CLR válidos, sin espacios ni puntuación.

 Conservar estas clases es especialmente útil:

- La clase raíz aparece en la esquina superior izquierda del diagrama de definición de DSL, en **Clases y relaciones**. Asígnele otro nombre según el DSL. Por ejemplo, un DSL denominado **MusicLibrary podría** tener una clase raíz denominada **Music**.

- La clase de diagrama aparece en la parte inferior derecha del diagrama de definición de DSL, en la **columna Elementos del** diagrama. Quizás tenga que desplazarse a la derecha para verlo. Normalmente se denomina _YourDsl_**Diagram**.

- Si usó la plantilla **Flujo** de tareas y desea crear diagramas con calles, mantenga y cambie el nombre de la clase de dominio Actor y la forma ActorSwimlane.

  Elimine o cambie el nombre de otras clases para que se ajusten a sus necesidades.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> Patrones para definir un DSL
 Le recomendamos que desarrolle un DSL agregando o ajustando una o dos características cada vez. Agregue una característica, ejecute el DSL y pruébelo y, después, agregue una o dos características más. Una característica típica de su DSL podría ser:

- Una clase de dominio, la relación de incrustación que conecta el elemento con el modelo, la forma necesaria para mostrar elementos de esa clase en el diagrama y la herramienta de elemento que permite a los usuarios crear elementos.

- Las propiedades de dominio de una clase de dominio y los elementos Decorator que los muestran en una forma.

- Una relación de referencia y el conector que la muestra en el diagrama, y la herramienta de conector que permite a los usuarios crear vínculos.

- Una personalización que requiere código de programa, como una restricción de validación o un comando de menú.

  En las secciones siguientes se describe cómo construir los tipos de características DSL más útiles. Hay muchos otros patrones con los que se puede construir un DSL, pero estos son los que se usan con más frecuencia.

> [!NOTE]
> Después de agregar una característica,  no olvide hacer clic en Transformar todas las plantillas en la barra de herramientas de Explorador de soluciones antes de compilar y ejecutar el DSL.

 La figura siguiente muestra las clases y relaciones que forman parte del DSL y que se usan como ejemplo en este tema.

 ![Relaciones de incrustación y referencia](../modeling/media/music_classes.png)

 La siguiente figura es un modelo de ejemplo de este DSL:

 ![Modelo de instancia de DSL generado](../modeling/media/music_instance.png)

> [!NOTE]
> Con "modelo" nos referimos a una instancia de su DSL que los usuarios crean y que normalmente se muestra como un diagrama. En este tema se explican tanto el diagrama DSL Definition (Definición de DSL) como los diagramas de modelo que aparecen cuando se usa su DSL.

## <a name="defining-domain-classes"></a><a name="classes"></a> Definir clases de dominio
 Las clases de dominio representan los conceptos de su DSL. Las instancias son elementos *del modelo*. Por ejemplo, en un **DSL de MusicLibrary,** podría tener clases de dominio **denominadas Album** y **Song**.

 Para crear una clase de dominio, puede arrastrar desde la herramienta **Clase de** dominio con nombre al diagrama y, a continuación, cambiar el nombre de la clase.

 Para obtener más información, vea [Propiedades de las clases de dominio](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Crear una relación incrustada para cada clase de dominio
 Todas las clases de dominio, excepto la clase raíz, deben ser el destino de al menos una relación de incrustación, o deben heredar de una clase que sea el destino de una relación de incrustación.

 En un modelo, todos los elementos de modelo son nodos de un único árbol de relaciones incrustadas. El origen y el destino de una relación de incrustación suelen denominarse clases primaria y secundaria.

 La selección de una clase primaria para una clase de dominio depende de cómo quiere que la duración de sus elementos dependa de otros elementos. Si se elimina un nodo de un árbol, normalmente también se elimina su subárbol. Por lo tanto, las clases de elemento que tienen una existencia independiente se incrustan directamente debajo de la clase raíz.

 Normalmente, si muestra un elemento dentro de otro elemento, quiere indicar una relación de propiedad. En ese caso, la clase primaria más apropiada es la clase del contenedor. La excepción es cuando el elemento que ve dentro del contendor es tan solo un vínculo de referencia a un elemento independiente. En ese caso, al eliminar el contenedor se elimina la referencia pero no el destino.

 En los patrones de una definición de DSL que se describen en este tema, damos por hecho que los elementos que se muestran dentro de un contenedor se eliminarán cuando el contenedor se elimine. Se pueden lograr esquemas más complejos mediante la definición de reglas.

|Cómo se muestra el elemento|Clase primaria (incrustación)|Ejemplo en la plantilla de solución de DSL|
|-|-|-|
|Forma en el diagrama<br /><br /> Calle.|Clase raíz del DSL.|Minimal Language.<br /><br /> Flujo de tareas: clase de actor.|
|Forma en una calle.|Clase de dominio de los elementos que se muestran como calles.|Flujo de tareas: clase de tarea.|
|Elemento en una lista en una forma; el elemento se elimina si el contenedor se elimina.<br /><br /> Puerto en el borde de una forma.|Clase de dominio que se asigna a la forma del contenedor.|Diagrama de clases: Clase de atributo.<br /><br /> Diagrama de componentes: Clase port.|
|Elemento en una lista; no se elimina si el contenedor se elimina.|Clase raíz del DSL.<br /><br /> La lista muestra vínculos de referencia.||
|No se muestra directamente.|Clase de la que forma parte.||

 En el ejemplo de la biblioteca de música, los álbumes se muestran como rectángulos en los que se enumeran los títulos de las canciones. Por lo tanto, la clase primaria de Album es la clase raíz Music, y la clase primaria de Song es Album.

 Para crear una clase de dominio y su inserción al mismo tiempo, haga clic en la herramienta **Relación** de inserción, haga clic en la clase primaria y, a continuación, haga clic en una parte en blanco del diagrama.

 Normalmente no es necesario ajustar el nombre de la relación de incrustación y de sus roles, porque rastrearán los nombres de las clases automáticamente.

 Para obtener más información, [vea Propiedades de relaciones de dominio](../modeling/properties-of-domain-relationships.md) y Propiedades de roles de [dominio.](../modeling/properties-of-domain-roles.md)

> [!NOTE]
> Incrustación no es lo mismo que herencia. En una relación de incrustación, las clases secundarias no heredan las características de sus primarias.

### <a name="add-domain-properties-to-each-domain-class"></a>Agregar propiedades de dominio a cada clase de dominio
 Las propiedades de dominio almacenan valores. Algunos ejemplos son: Nombre, Título, Fecha de publicación.

 Haga **clic en Propiedades** del dominio en la clase , presione la tecla ENTRAR y escriba el nombre de una propiedad. El tipo predeterminado de una propiedad de dominio es String. Si desea cambiar el tipo, seleccione la propiedad de dominio y establezca **tipo en** la **ventana** Propiedades. Si el tipo que desea no está en la lista desplegable, vea [Adding Property Types](#addTypes).

 **Establezca una propiedad Element Name (Nombre de elemento).**  Seleccione una propiedad de dominio que se pueda usar para identificar los elementos en el explorador del lenguaje. Por ejemplo, en la clase de dominio Song que pueda seleccionar la propiedad de dominio Title (Título). En la **ventana Propiedades,** establezca **Is Element Name** en `true` .

### <a name="create-derived-domain-classes"></a>Crear clases de dominio derivadas
 Si quiere que una clase de dominio tenga variantes que hereden sus propiedades y relaciones, cree clases que deriven de ella. Por ejemplo, Album podría tener las clases derivadas WMA y MP3.

 Cree la clase derivada mediante la herramienta **Clase de** dominio.

 Haga clic en **la herramienta** Herencia, haga clic en la clase derivada y, a continuación, haga clic en la clase base.

 Considere la posibilidad de **establecer el modificador de** herencia de la clase base para **abstraer**. Si cree que puede necesitar instancias de la clase base, considere la posibilidad de crear en su lugar una clase derivada diferente para ellas.

 Las clases derivadas heredan las propiedades y los roles de sus clases base.

### <a name="tidy-the-dsl-definition-diagram"></a>Ordenar el diagrama DSL Definition (Definición de DSL)
 Cuando se agregan relaciones, algunas de las clases aparecen en más de un lugar. Para reducir el número de apariencias y ampliar el diagrama, haga clic con el botón derecho en la clase de destino de una relación y, a continuación, haga clic en **Bring Tree Here (Traer árbol aquí).** Para el efecto contrario, haga clic con el botón derecho en la clase de destino de una relación y haga clic **en Dividir árbol.** Si no ve estos comandos del menú, asegúrese de que solo está seleccionada la clase de dominio.

 Use CTRL+Flecha arriba y CTRL+Flecha abajo para mover las clases de dominio y las clases de forma.

### <a name="test-the-domain-classes"></a>Probar las clases de dominio

##### <a name="to-test-the-new-domain-classes"></a>Para probar las nuevas clases de dominio

1. **Haga clic en Transformar todas las** plantillas en la barra de herramientas Explorador de soluciones, para generar el código del diseñador DSL. Este paso se puede automatizar. Para obtener más información, [vea How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. **Compile y ejecute el DSL.** Presione F5 o CTRL+F5 para ejecutar una nueva instancia de Visual Studio en modo experimental. En la instancia experimental de Visual Studio, abra o cree un archivo que tenga la extensión de nombre de archivo del DSL.

3. **Abra el explorador.** En el lado del diagrama se encuentra la ventana del explorador de idiomas, que normalmente se denomina *Explorador de Idiomas.* Si no ve esta ventana, podría estar en una pestaña debajo del Explorador de soluciones. Si no lo encuentra,  en el menú Ver, seleccione Otras **ventanas** y, a continuación, haga clic *en YourLanguage* **Explorer (Explorador** de Idioma).

     El explorador presenta una vista de árbol del modelo.

4. **Crear nuevos elementos.** Haga clic con el botón derecho en el nodo raíz de la parte superior y, a continuación, **haga clic en Agregar nueva**_clase._

     En el explorador del lenguaje aparece una nueva instancia de su clase.

5. Cuando cree nuevas instancias, compruebe que cada instancia tenga un nombre diferente. Esto solo se producirá si ha establecido la marca **Is Element Name** en una propiedad de dominio.

6. **Examine las propiedades del dominio. Con una instancia de la clase seleccionada,** inspeccione el ventana Propiedades. Debe mostrar las propiedades de dominio que ha definido en esta clase de dominio.

7. **Guarde el archivo, cierre y vuelva a abrirlo.** Después de expandir los nodos en el explorador, todas las instancias creadas deben ser visibles.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Definir formas en el diagrama
 Puede definir clases de elementos que aparecen en un diagrama, como rectángulos, elipses o iconos.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Para definir una clase de elementos que aparecen como formas en un diagrama

1. **Defina y pruebe una clase de dominio como se describe en**  [Definición de clases de dominio](#classes) **.**

   - La clase primaria debería ser la clase raíz. Es decir, debería haber una relación de incrustación entre la clase raíz y la nueva clase de dominio.

   - Si el diagrama tiene calles, la clase primaria puede ser la clase de dominio que está asignada a una calle. Antes de continuar con este procedimiento, consulte [Definición de un DSL que tiene Calles.](#swimlanes)

2. **Agregue una clase de forma** para representar los elementos del diagrama del modelo. Arrastre desde una de las siguientes herramientas al diagrama DSL Definition (Definición de DSL):

   - **Forma de geometría** proporciona un rectángulo o elipse.

   - **Forma de imagen** muestra una imagen que se proporciona.

   - **Forma de** compartimiento es un rectángulo que contiene una o varias listas de elementos.

     Cambie el nombre de la clase de forma, que aparecerá en el lado derecho del diagrama DSL Definition (Definición de DSL), en Shapes and Connectors (Formas y conectores).

3. **Defina una imagen, si ha creado una forma de imagen**.

   1. Cree un archivo de imagen de cualquier tamaño. Se admiten los formatos BMP, JPEG, GIF y EMF.

   2. En el Explorador de soluciones, agregue el archivo a la solución, en Dsl\Resources.

   3. Vuelva al diagrama DSL Definition (Definición de DSL) y seleccione la nueva clase de forma de imagen.

   4. En la ventana Propiedades, haga clic en la **propiedad** Imagen.

   5. En el **cuadro de diálogo Seleccionar** imagen , haga clic en el menú desplegable bajo Nombre de **archivo** y seleccione la imagen.

4. **Agregar elementos Decorator de texto a la forma para mostrar las propiedades de dominio.**

    Para mostrar el nombre o el título del elemento de modelo, probablemente necesitará al menos un elemento Decorator de texto.

    Haga clic con el botón derecho en el encabezado de la clase de forma, seleccione **Agregar** y, a continuación, haga clic en **Decorador de texto.** Establezca el nombre del decorador y, en la ventana Propiedades establezca su **posición**.

5. **Conecte cada forma con un mapa de elementos de diagrama a la clase de dominio que debe mostrar.**

    Haga clic en **la herramienta Diagrama de mapa de** elementos, haga clic en la clase de dominio y, a continuación, haga clic en la clase de forma.

6. **Asigne las propiedades a los elementos Decorator de texto.**

   1. Seleccione la línea gris entre la clase de dominio y la clase de forma que representa la asignación de elemento de diagrama.

   2. En la **ventana Detalles de DSL,** haga clic en la **pestaña Decorator Maps (Mapas de decorador).** Si no ve la ventana Detalles  de **DSL,** en el menú Ver, seleccione Otras **ventanas** y, a continuación, haga clic en **Detalles de DSL**. Normalmente es necesario levantar la parte superior de esta ventana para ver todo su contenido.

   3. Seleccione el nombre de un elemento Decorator. En **Mostrar propiedad**, seleccione el nombre de una propiedad de la clase de dominio. Repita este paso para cada elemento Decorator.

       Si desea mostrar una propiedad de un elemento relacionado, haga clic en el navegador del árbol desplegable en **Ruta de acceso para mostrar la propiedad**.

   4. Asegúrese de que hay una marca de verificación junto al nombre de cada elemento Decorator.

      ![Ventana de asignaciones de formas y detalles de DSL](../modeling/media/dsldetailswindow.png)

7. **Cree un elemento de cuadro de herramientas para crear los elementos de la clase de dominio.**

   1. En **el Explorador de DSL,** expanda el nodo **Editor** y todos sus subnúdulos.

   2. Haga clic con el botón derecho en el nodo bajo **Pestañas del cuadro de herramientas** que tenga el mismo nombre que el DSL, por ejemplo MusicLibrary. Haga clic **en Agregar herramienta de elemento**.

       > [!NOTE]
       > Si hace clic con el botón derecho **en el nodo** Herramientas, no verá La herramienta Agregar **elemento**. En su lugar, haga clic en el nodo situado encima de él.

   3. En la ventana Propiedades con la nueva herramienta de elemento seleccionada, establezca **Clase** en la clase de dominio que ha agregado recientemente.

   4. Establezca **Título e** Información sobre **herramientas.**

   5. Establezca **Icono del cuadro de** herramientas en un icono que aparecerá en el cuadro de herramientas. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

        Para crear un icono, abra Dsl\Resources **en Explorador de soluciones**. Copie y pegue uno de los archivos BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

        Vuelva al diagrama de definición de DSL, seleccione la herramienta y, en la ventana Propiedades haga clic **en [...] en icono** del cuadro de **herramientas**. En el **cuadro de diálogo** Seleccionar mapa de bits, seleccione .BMP archivo en el menú desplegable.

   Para obtener más información, vea [Propiedades de formas de geometría y](../modeling/properties-of-geometry-shapes.md) Propiedades de formas de [imagen.](../modeling/properties-of-image-shapes.md)

#### <a name="to-test-shapes"></a>Para probar las formas

1. **Haga clic en Transformar todas las** plantillas en la barra Explorador de soluciones, para generar el código del diseñador DSL.

2. **Compile y ejecute el DSL.** Presione F5 o CTRL+F5 para ejecutar una nueva instancia de Visual Studio en modo experimental. En la instancia experimental de Visual Studio, abra o cree un archivo que tenga la extensión de nombre de archivo del DSL.

3. **Compruebe que las herramientas de elemento aparecen en el cuadro de herramientas.**

4. **Cree formas** arrastrando desde una herramienta hasta el diagrama del modelo.

5. **Compruebe que aparece cada decorador de texto y** que:

   1. Puede editarlo, a menos que haya establecido la marca **Is UI Read Only** (Solo lectura de IU) en la propiedad de dominio.

   2. Cuando se edita la propiedad en la ventana Properties (Propiedades) o en el elemento Decorator, la otra vista se actualiza.

   Después de probar una forma por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. Para obtener más información, [vea Personalizar y extender un Domain-Specific lenguaje .](../modeling/customizing-and-extending-a-domain-specific-language.md)

## <a name="defining-reference-relationships"></a><a name="references"></a> Definir relaciones de referencia
 Puede definir una relación de referencia entre cualquier clase de dominio de origen y cualquier clase de dominio de destino. Las relaciones de referencia suelen mostrarse en un diagrama como conectores, que son líneas entre formas.

 Por ejemplo, si los álbumes y los artistas se muestran como formas en el diagrama, podría definir una relación llamada ArtistsAppearedOnAlbums que vincula los artistas con los álbumes en los que han trabajado. Vea el ejemplo en la figura.

 ![Modelo de instancia de DSL generado](../modeling/media/music_instance.png)

 Las relaciones de referencia también pueden vincular elementos del mismo tipo. Por ejemplo, en un DSL que representa un árbol genealógico, la relación entre los padres y los hijos es una relación de referencia de persona a persona.

### <a name="define-a-reference-relationship"></a>Definir una relación de referencia
 Haga clic en la herramienta Reference Relationship (Relación de referencia), haga clic en la clase de dominio de origen de la relación y, después, haga clic en la clase de dominio de destino. La clase de destino puede ser la misma que la clase de origen.

 Cada relación tiene dos roles, representados por la línea a cada lado del cuadro de relación. Puede seleccionar cada rol y establecer sus propiedades en la ventana Properties (Propiedades).

 **Considere la posibilidad de cambiar el nombre de los roles**. Por ejemplo, en una relación entre personas, quizás quiera cambiar los nombres predeterminados por Padres e Hijos, Director y Subordinados, Profesor y Estudiante, etc.

 **Ajuste las multiplicidades de cada rol,** si es necesario. Si quiere que cada persona tenga al menos un director, establezca la multiplicidad que aparece debajo de la etiqueta Director en el diagrama a 0..1.

 **Agregue propiedades de dominio a la relación.**  En la figura, la relación Artist-Album tiene una propiedad de rol.

 **Establezca la propiedad Allows Duplicates** de la relación, si puede haber más de un vínculo de la misma clase entre el mismo par de elementos del modelo. Por ejemplo, podría permitir que un Profesor enseñe más de una Asignatura al mismo Estudiante.

 ![Asignaciones de formas para conectores](../modeling/media/music_connector.png)

 Para obtener más información, [vea Propiedades de relaciones de dominio](../modeling/properties-of-domain-relationships.md) y Propiedades de roles de [dominio](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Definir un conector para mostrar la relación
 Un conector muestra una línea entre dos formas en el diagrama del modelo.

 Arrastre la herramienta **Conector** al diagrama de definición de DSL.

 Agregue elementos Decorator de texto si quiere mostrar etiquetas en el conector. Establezca sus posiciones. Para permitir que el usuario mueva un decorador de texto, establezca su **propiedad Is Moveable.**

 Use la **herramienta Diagrama de mapa de elementos** para vincular el conector a la relación de referencia.

 Con el mapa de elementos de diagrama seleccionado, abra la **ventana Detalles de DSL** y abra la pestaña **Decorator Maps (Mapas de decorador).**

 Seleccione cada **decorator y** establezca **Mostrar propiedad** en la propiedad de dominio correcta.

 Asegúrese de que aparece una marca de verificación junto a cada elemento de la **lista Decorators.**

### <a name="define-a-connection-builder-tool"></a>Definir una herramienta Connection Builder (Generador de conexiones)
 En la **ventana Explorador de DSL,** expanda el **nodo Editor** y todos sus subnodos.

 Haga clic con el botón derecho en el nodo que tiene el mismo nombre que el DSL y, a continuación, haga clic **en Agregar nueva herramienta de conexión**.

 Con la nueva herramienta seleccionada, en la ventana Properties (Propiedades):

- Establezca el **título y** la información **sobre herramientas.**

- Haga **clic en Generador de** conexiones y seleccione el generador adecuado para la nueva relación.

- Establezca **Icono del cuadro de** herramientas en el icono que desea que aparezca en el cuadro de herramientas. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

     Para crear un icono, abra Dsl\Resources **en Explorador de soluciones**. Copie y pegue uno de los archivos BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

     Vuelva al diagrama de definición de DSL, seleccione la herramienta y, en la ventana Propiedades haga clic **en [...] en icono** del cuadro de **herramientas**. En el **cuadro de diálogo** Seleccionar mapa de bits, seleccione .BMP archivo en el menú desplegable.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Para probar una relación de referencia y un conector

1. **Haga clic en Transformar todas las** plantillas en la barra Explorador de soluciones, para generar el código del diseñador DSL.

2. **Compile y ejecute el DSL.** Presione F5 o CTRL+F5 para ejecutar una nueva instancia de Visual Studio en modo experimental. En la instancia experimental de Visual Studio, abra o cree un archivo que tenga la extensión de nombre de archivo del DSL.

3. **Compruebe que la herramienta de conexión aparece en el cuadro de herramientas.**

4. **Cree formas** arrastrando desde una herramienta hasta el diagrama del modelo.

5. **Cree conexiones** entre las formas. Haga clic en la herramienta de conector, en una forma y, después, en otra forma.

6. **Compruebe que no puede crear conexiones entre clases inapropiadas.**  Por ejemplo, si su relación es entre Albums y Artists, compruebe que no puede vincular Artists con Artists.

7. **Compruebe que las multiplicidades son correctas. Por ejemplo, compruebe que no puede conectar una persona a más de un administrador.**

8. **Compruebe que aparece cada decorador de texto y** que:

   1. Puede editarlo, a menos que haya establecido la marca **Is UI Read Only** (Solo lectura de IU) en la propiedad de dominio.

   2. Cuando se edita la propiedad en la ventana Properties (Propiedades) o en el elemento Decorator, la otra vista se actualiza.

   Después de probar un conector por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. Para obtener más información, [vea Personalizar y extender un Domain-Specific lenguaje .](../modeling/customizing-and-extending-a-domain-specific-language.md)

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Definir formas que contienen listas: formas de compartimiento
 Una forma de compartimiento contiene una o varias listas de elementos. Por ejemplo, en un DSL de biblioteca de música, podría usar formas de compartimiento para representar álbumes de música. En cada álbum, hay una lista de canciones.

 ![Forma de compartimiento](../modeling/media/compartmentshape.png)

 En el método más sencillo de lograr este efecto en una definición de DSL, se define una clase de dominio para el contenedor y una clase de dominio para cada lista. La clase de contenedor se asigna a la forma de compartimiento.

 ![Asignación de formas](../modeling/media/music_mapcomp.png)

 Para obtener más información, vea [Propiedades de formas de compartimiento.](../modeling/properties-of-compartment-shapes.md)

#### <a name="to-define-a-compartment-shape"></a>Para definir una forma de compartimiento

1. **Cree la clase de dominio de contenedor**. Haga clic **en la herramienta Relación** de inserción, haga clic en la clase raíz del modelo y, a continuación, haga clic en una parte en blanco del diagrama de definición de DSL. Esto crea la clase de dominio llamada Album en la figura de ejemplo.

     En lugar de incrustarlo en la clase raíz, también puede incrustar el contenedor en una clase de dominio que esté asignada a una calle.

     Agregue una propiedad de dominio como Name a la clase y establezca su **marca Is Element Name** en el ventana Propiedades.

2. **Cree la clase de dominio de elemento de lista**. Haga clic **en la herramienta Relación de** inserción, haga clic en la clase contenedora (Album) y, a continuación, haga clic en una parte en blanco del diagrama. Esto crea la clase de dominio llamada Song en la figura de ejemplo.

     Agregue una propiedad de dominio como Title a la clase y establezca su **marca Is Element Name.**

     Agregue otras propiedades de dominio.

     Agregue otra clase de dominio de elemento de lista para cada lista que quiera mostrar.

3. **Para mezclar varios tipos de elemento en la lista,** cree clases que hereden de la clase de lista. Haga que la clase de lista sea abstracta estableciendo su **modificador de herencia**.

     Por ejemplo, si quiere que la música clásica se ordene por compositor en lugar de por artista, podría crear dos subclases de Song, ClassicalSong y NonClassicalSong.

4. **Cree la forma del compartimiento**. Arrastre desde la herramienta **Forma de compartimiento** hasta el diagrama de definición de DSL.

     Agregue un elemento Decorator de texto y establezca su nombre.

     Agregue un compartimiento y establezca su nombre.

5. Para permitir que el usuario oculte los compartimientos de lista, haga clic con el botón derecho en la clase de forma del compartimiento, seleccione Agregar y, a continuación, haga clic **en Expandir o contraer decorator**. En la ventana Properties (Propiedades), establezca la posición del elemento Decorator.

6. Haga clic en **la herramienta Diagrama de mapa de** elementos, haga clic en la clase de dominio de contenedor y, a continuación, haga clic en la forma del compartimiento.

7. Seleccione el vínculo de la asignación de elemento de diagrama entre la clase de dominio y la forma. En la **ventana Detalles de DSL:**

    1. Haga clic **en la pestaña Decorators (Decoradores).** Haga clic en el nombre del decorador y, a continuación, seleccione el elemento adecuado en **Mostrar propiedad**. Asegúrese de que haya una marca de verificación junto al nombre del elemento Decorator.

    2. Haga clic en **la pestaña Mapas de** compartimiento.

         Haga clic en el nombre del compartimiento.

         En **Ruta de acceso de la colección Elementos mostrados**, vaya a la clase de elemento de lista (Canción). Haga clic en la flecha hacia abajo para usar la herramienta de navegador.

         En **Mostrar propiedad**, seleccione la propiedad que debe mostrarse en la lista. En el ejemplo, es Title.

> [!NOTE]
> Use los campos Path (Ruta de acceso) del Decorator Map (Asignación de elemento Decorator) y los campos de Compartment Maps (Asignaciones de compartimientos) para crear relaciones más complejas entre las clases de dominio y la forma de compartimiento.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Para definir una herramienta para crear la forma

1. **Cree un elemento de cuadro de herramientas para crear los elementos de la clase de dominio.**

2. En **el Explorador de DSL,** expanda el nodo **Editor** y todos sus subnúdulos.

3. Haga clic con el botón derecho en el nodo bajo **Pestañas del cuadro de herramientas** que tenga el mismo nombre que el DSL, por ejemplo MusicLibrary. Haga clic **en Agregar herramienta de elemento**.

    > [!NOTE]
    > Si hace clic con el botón derecho **en el nodo** Herramientas, no verá La herramienta Agregar **elemento**. En su lugar, haga clic en el nodo situado encima de él.

4. En la ventana Propiedades con la nueva herramienta de elemento seleccionada, establezca **Clase** en la clase de dominio que ha agregado recientemente.

5. Establezca **Título e** Información sobre **herramientas.**

6. Establezca **Icono del cuadro de** herramientas en un icono que aparecerá en el cuadro de herramientas. Puede establecerlo en un icono nuevo o en un icono que ya se haya usado para otra herramienta.

     Para crear un icono, abra Dsl\Resources **en Explorador de soluciones**. Copie y pegue uno de los archivos .BMP existentes de las herramientas de elemento. Cambie el nombre a la copia pegada y, después, haga doble clic en él para editarlo.

     Vuelva al diagrama de definición de DSL, seleccione la herramienta y, en la ventana Propiedades haga clic **en [...] en icono** del cuadro de **herramientas**. En el **cuadro de diálogo** Seleccionar mapa de bits, seleccione el archivo BMP en el menú desplegable.

#### <a name="to-test-a-compartment-shape"></a>Para probar una forma de compartimiento

1. **Haga clic en Transformar todas las** plantillas en la barra Explorador de soluciones, para generar el código del diseñador DSL.

2. **Compile y ejecute el DSL.** Presione F5 o CTRL+F5 para ejecutar una nueva instancia de Visual Studio en modo experimental. En la instancia experimental de Visual Studio, abra o cree un archivo que tenga la extensión de nombre de archivo del DSL.

3. **Compruebe que la herramienta aparece en el cuadro de herramientas.**

4. Arrastre la herramienta al diagrama del modelo. Se crea una forma.

    Compruebe que el nombre del elemento aparece y se establece automáticamente en un valor predeterminado.

5. Haga clic con el botón derecho en el encabezado de la nueva forma y, a continuación, haga clic en *Agregar el elemento de lista.* En el ejemplo, el comando es Add Song (Agregar canción).

    Compruebe que aparece un elemento en la lista y que tiene un nombre nuevo.

6. Haga clic en uno de los elementos de lista y, después, examine la ventana Properties (Propiedades). Verá las propiedades de los elementos de lista.

7. Abra el explorador del lenguaje. Compruebe que puede ver los nodos de contenedor con los nodos de elemento de lista dentro.

   ![Explorador generado de DSL](../modeling/media/music_explorer.png)

   Después de probar una forma de compartimiento por primera vez, quizás quiera ajustar algunas de sus propiedades y agregar algunas características más avanzadas. Para obtener más información, [vea Personalizar y extender un Domain-Specific lenguaje .](../modeling/customizing-and-extending-a-domain-specific-language.md)

### <a name="displaying-a-reference-link-in-a-compartment"></a>Mostrar un vínculo de referencia en un compartimiento
 Normalmente, un elemento que se muestra en un compartimiento es un elemento secundario del elemento que está representado por la forma de compartimiento. Pero a veces querrá mostrar un elemento que está vinculado a él con una relación de referencia.

 Por ejemplo, podríamos agregar un segundo compartimiento a AlbumShape que muestra una lista de los artistas que están vinculados al álbum.

 En este caso, el compartimiento debe mostrar el vínculo en lugar del elemento referenciado. El motivo es que quiere que, cuando el usuario seleccione el elemento en el compartimiento y presione Supr, se elimine el vínculo, no el elemento referenciado.

 En cualquier caso, puede hacer que se muestre el nombre del elemento referenciado en el compartimiento.

 En el procedimiento siguiente se da por hecho que ya ha creado la clase de dominio, la relación de referencia, la forma de compartimiento y la asignación de elemento de diagrama, tal y como se describió anteriormente en esta sección.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Para mostrar un vínculo de referencia en un compartimiento

1. **Agregue un compartimiento a la forma del compartimiento**. En el diagrama de definición de DSL, haga clic con el botón derecho en la clase de forma del compartimiento, seleccione **Agregar** y, a continuación, haga clic en **Compartimiento**.

2. Establezca **Ruta de acceso de la colección Elementos mostrados** para navegar al vínculo, en lugar de a su elemento de destino. Haga clic en el menú desplegable y use la vista de árbol para seleccionar la relación de referencia en lugar de su destino. En el ejemplo, la relación **es ArtistAppearedOnAlbums**.

3. Establezca **Ruta de acceso en Mostrar** propiedad para navegar desde el vínculo al elemento de destino. En el ejemplo, se trata de **Artist**.

4. Establezca **Display Property en** la propiedad adecuada del elemento de destino, por ejemplo **Name**.

5. **Transforme Todas las plantillas,** compile y ejecute el DSL y abra un modelo de prueba.

6. En el diagrama del modelo, cree las clases de forma apropiadas, establezca sus nombres y cree un vínculo entre ellas. En la forma de compartimiento, deben aparecer los nombres de los elementos vinculados.

7. Seleccione el vínculo o el elemento en la forma de compartimiento. Deben desaparecer tanto el vínculo como el elemento.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Definir puertos en el límite de otra forma
 Un puerto es una forma que está situada en los límites de otra forma.

 Los puertos se pueden usar para proporcionar un punto de conexión fijo en otra forma al cual el usuario puede dibujar conectores. En este caso, puede hacer que la forma de puerto sea transparente.

 Para ver un ejemplo en el que se usan puertos, seleccione la plantilla **Diagrama de componentes** al crear una nueva solución DSL. En este ejemplo se muestran los principales aspectos para tener en cuenta al definir puertos:

- Hay una clase de dominio que representa el contenedor de los puertos, `Component`.

- Hay una clase de dominio que representa los puertos. en el ejemplo es `ComponentPort`.

- Hay una relación de incrustación desde la clase de dominio de contendor a la clase de dominio de puerto. Para obtener más información, vea [Definición de clases de dominio](#classes).

- Si quiere mezclar diferentes tipos de puerto en el mismo contenedor, puede crear subclases de la clase de dominio de puerto. En el ejemplo, `InPort` y `OutPort` heredan de `ComponentPort`.

- La clase de dominio de contenedor se puede asignar a cualquier tipo de forma. En el ejemplo, es `ComponentShape`. Para obtener más información, vea [Definición de formas.](#shapes)

- Las clases de dominio de puerto se asignan a formas de puerto. Puede asignar las clases derivadas a clases de forma de puerto diferentes, o asignar la clase base a una clase de forma de puerto.

  En otros aspectos, las formas de puerto se comportan como se describe en [Definición de formas](#shapes).

  Para obtener más información, vea [Propiedades de formas de puerto.](../modeling/properties-of-port-shapes.md)

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Definición de un DSL que tiene calles
 Las calles son una partición horizontal o vertical de un diagrama. Cada calle corresponde a un elemento de modelo. Su definición de DSL requiere una clase de dominio para los elementos de calle.

 La mejor manera de crear un DSL con calles es crear una nueva solución de DSL y elegir la plantilla de solución Task Flow (Flujo de tareas). En la definición de DSL, la clase Actor es la clase de dominio asignada a la calle. Cambie el nombre de esta y otras clases para adaptarlas a su proyecto.

 Para agregar una clase que se mostrará como una forma dentro de una calle, cree una relación de incrustación entre la clase de calle y la nueva clase. Los usuarios podrán arrastrar elementos desde una calle a otra, pero cada elemento siempre estará dentro de una calle determinada. En la plantilla de solución Task Flow (Flujo de tareas), FlowElement es una clase secundaria de la clase de calle.

 Para agregar una clase que se mostrará como una forma independiente de las calles, cree una relación de incrustación entre la clase raíz y la nueva clase. Los usuarios podrán colocar estas formas en cualquier lugar del diagrama, incluso traspasando los límites de las calles y fuera de ellas. En la plantilla de solución Task Flow (Flujo de tareas), Comment es una clase secundaria de la clase raíz.

 Para obtener más información, [vea Properties of Swimlanes](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Agregar tipos de propiedad

### <a name="domain-enumerations-and-literals"></a>Literales y enumeradores de dominio
 Una enumeración de dominio es un tipo con varios valores literales.

 Para agregar una enumeración de dominio, haga clic con el botón derecho en la raíz del modelo en el Explorador **DSL** y, a continuación, haga clic **en Agregar nueva enumeración de dominio**. El elemento aparecerá en el Explorador **de DSL en** el nodo Tipos **de** dominio. Este elemento no aparece en el diagrama.

 Para agregar literales de enumeración a la enumeración de dominio, haga clic con el botón derecho en la enumeración de dominios en el Explorador **dsl** y, a continuación, haga clic **en Agregar nuevo literal de enumeración**.

 De forma predeterminada, una propiedad que tiene un tipo de enumeración solo se puede establecer en un valor de la enumeración al mismo tiempo. Si desea que los usuarios y programadores puedan establecer cualquier combinación de valores(un "campo de bits") establezca la propiedad **IsFlags** de la enumeración .

### <a name="external-types"></a>Tipos externos
 Al establecer el tipo de una propiedad de dominio, si  no encuentra el tipo que desea en la lista desplegable Tipo, puede agregar un tipo externo. Por ejemplo, podría agregar el tipo **System.Drawing.Color** a la lista.

 Para agregar un tipo, haga clic con el botón derecho en la raíz del modelo en el Explorador DSL y, a continuación, haga clic **en Agregar nuevo tipo externo**. En la ventana Propiedades, establezca el nombre en **Color** y el espacio de nombres en **System.Drawing**. Este tipo aparece ahora en el Explorador de DSL en **Tipos de dominio**. Puede elegirlo siempre que establezca el tipo de una propiedad de dominio.

## <a name="customizing-the-dsl"></a><a name="custom"></a> Personalización del DSL
 Con las técnicas descritas en este tema, puede crear rápidamente un DSL con una notación en forma de diagrama, un formato XML legible, y las herramientas básicas que se necesitan para generar código y otros artefactos.

 Hay dos métodos para extender la definición de DSL:

1. Ajuste el DSL usando más características de la definición de DSL. Por ejemplo, puede crear una sola herramienta de conector que pueda crear varios tipos de conector, y puede controlar las reglas por las que al eliminar un elemento también se eliminan los elementos relacionados. Estas técnicas se logran principalmente estableciendo valores en la definición de DSL, y algunas requieren unas cuantas líneas de código de programa.

     Para obtener más información, [vea Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Amplíe sus herramientas de modelado usando código de programa para lograr efectos más avanzados. Por ejemplo, puede crear comandos de menú que pueden cambiar el modelo, y puede crear herramientas que integren dos o más DSL. VMSDK está diseñado específicamente para facilitar la integración de las extensiones con el código que se genera a partir de la definición de DSL.  Para obtener más información, vea [Escribir código para personalizar un Domain-Specific lenguaje .](../modeling/writing-code-to-customise-a-domain-specific-language.md)

### <a name="changing-the-dsl-definition"></a>Cambiar la definición de DSL
 Cuando se crea un elemento en una definición de DSL, muchos valores predeterminados se establecen automáticamente. Una vez establecidos, puede cambiarlos. Esto simplifica el desarrollo de un DSL, al tiempo que permite realizar personalizaciones eficaces.

 Por ejemplo, cuando se asigna una forma a un elemento, la ruta del elemento primario de la asignación se establece automáticamente de acuerdo con la relación de incrustación de la clase de dominio. Sin embargo, si más adelante cambia la relación de incrustación, la ruta del elemento primario no cambia automáticamente.

 Por lo tanto, debe tener en cuenta que, cuando se cambian algunas relaciones en una definición de DSL, no es extraño que aparezcan errores al guardar la definición o al transformar todas las plantillas. La mayoría de estos errores son fáciles de corregir. Haga doble clic en el informe de error para ver la ubicación del error.

 Vea también [Cómo: Cambiar el espacio de nombres de un Domain-Specific lenguaje](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Solucionar problemas
 En la tabla siguiente se enumeran algunos de los problemas más comunes que se encuentran al diseñar un DSL, además de sugerencias para solucionarlos. Puede obtener más consejos en el Foro [de extensibilidad de las herramientas de visualización](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

| Problema | Sugerencia |
|-|-|
| Los cambios que he hecho en el archivo de definición de DSL no surten efecto. | Haga **clic en Transformar todas las** plantillas en la barra de herramientas Explorador de soluciones y, a continuación, vuelva a generar la solución. |
| Las formas muestran el nombre de un elemento Decorator en lugar del valor de la propiedad. | Configure la asignación del elemento Decorator. En el diagrama DSL Definition (Definición de DSL), haga clic en la asignación de elemento de diagrama, que es la línea gris entre la clase de dominio y la clase de forma.<br /><br /> Abra la **ventana Detalles de DSL.** Si no puede verlo, en el menú Ver, seleccione Otras **ventanas** y, a continuación, haga clic en **Detalles de DSL**.<br /><br /> Haga clic en **la pestaña Decorator Maps (Mapas de decorador).** Seleccione el nombre del decorador. Asegúrese de que la casilla situada junto a él está activada. En **Mostrar propiedad**, seleccione el nombre de una propiedad de dominio.<br /><br /> Para obtener más información, vea [Formas en el diagrama](#shapes). |
| En DSL Explorer (Explorador de DSL), no puedo agregar nada a una colección. Por ejemplo, al hacer clic con el botón secundario en Tools (Herramientas), no hay ningún comando "Add Tool" (Agregar herramienta) en el menú.<br /><br /> En el explorador de mi DSL, no puedo agregar un elemento a una lista. | Haga clic en el elemento situado encima del nodo que está intentando. Cuando quiera agregar algo a una lista, el comando Add (Agregar) no está en el nodo de lista, sino en su propietario. |
| Creé una clase de dominio pero no puedo crear instancias en el explorador del lenguaje. | Todas las clases de dominio, excepto la raíz, deben ser el destino de una relación de incrustación. |
| En el explorador de mi DSL, los elementos se muestran solo con sus nombres de tipo. | En definición de DSL, seleccione una propiedad de dominio de la clase y, en la ventana Propiedades, establezca **Is Element Name** en true. |
| Mi DSL siempre se abre en el editor XML. | El motivo puede ser que se produjo un error mientras se leía el archivo. Sin embargo, después de corregir ese error, debe restablecer explícitamente el editor para que sea su diseñador de DSL.<br /><br /> Haga clic con el botón derecho en el elemento de proyecto, haga clic **en Abrir con** y seleccione *YourLanguage* Designer **(predeterminado).** |
| El cuadro de herramientas de mi DSL no aparece después de cambiar los nombres de ensamblado. | Inspeccione y actualice **DslPackage\GeneratedCode\Package.tt** Para obtener más información, vea [Cómo:](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md)Cambiar el espacio de nombres de un Domain-Specific language . |
| El cuadro de herramientas de mi DSL no aparece, pero no he cambiado el nombre del ensamblado.<br /><br /> O bien, se muestra un cuadro de mensaje que indica un error al cargar una extensión. | Restablezca la instancia experimental y vuelva a compilar la solución.<br /><br /> 1. En el cuadro de menú Inicio, en Todos los **programas,** expanda , herramientas y, a continuación, haga clic en Restablecer la Microsoft Visual Studio [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] Experimental **Instance**. <br />2. En el menú **Compilar** , haga clic en **Recompilar solución**. |

## <a name="see-also"></a>Vea también

- [Introducción a los lenguajes específicos de dominio](../modeling/getting-started-with-domain-specific-languages.md)
- [Crear lenguajes específicos de dominio basados en Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Crear lenguajes específicos de dominio basados en WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)
