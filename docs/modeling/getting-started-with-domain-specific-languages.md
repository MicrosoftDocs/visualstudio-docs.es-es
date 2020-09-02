---
title: Introducción a los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a4761703610a87818cd1512f96530a0f865faf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238548"
---
# <a name="get-started-with-domain-specific-languages"></a>Introducción a los lenguajes específicos de dominio

En este tema se explican los conceptos básicos de la definición y el uso de un lenguaje específico de dominio (DSL) creado con el SDK de modelado para Visual Studio.

> [!NOTE]
> El SDK de transformación de plantillas de texto y el SDK de modelado de Visual Studio se instalan automáticamente al instalar características específicas de Visual Studio. Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/) para obtener más información.

Si no está familiarizado con los DSL, se recomienda que trabaje en el **laboratorio de herramientas de DSL**, que puede encontrar en este sitio: SDK de [visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>¿Qué puede hacer con un lenguaje específico de dominio?

Un lenguaje específico de dominio es una notación, normalmente gráfica, que está diseñada para usarse con un fin determinado. Por el contrario, los lenguajes como UML son de uso general. En un DSL, puede definir los tipos de elemento de modelo y sus relaciones, y cómo se presentan en la pantalla.

Una vez que haya diseñado un DSL, puede distribuirlo como parte de un paquete de extensión de integración de Visual Studio (VSIX). Los usuarios trabajan con el DSL en Visual Studio:

![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt_instance.png)

La notación solo es parte de un DSL. Junto con la notación, el paquete VSIX incluye herramientas que los usuarios pueden aplicar para ayudarles a editar y generar material a partir de sus modelos.

Una de las aplicaciones principales de DSL es generar código de programa, archivos de configuración y otros artefactos. Especialmente en proyectos grandes y líneas de productos, donde se crearán varias variantes de un producto, la generación de muchos de los aspectos variables de los DSL puede proporcionar un aumento considerable de la confiabilidad y una respuesta muy rápida a los cambios en los requisitos.

El resto de esta información general es un tutorial que presenta las operaciones básicas de creación y uso de un lenguaje específico de dominio en Visual Studio.

## <a name="prerequisites"></a>Requisitos previos

Para definir un DSL, debe tener instalados los siguientes componentes:

| Componente | Vínculo |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| SDK de modelado para Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Crear una solución DSL

Para crear un nuevo lenguaje específico de dominio, cree una nueva solución de Visual Studio mediante la plantilla de proyecto de lenguaje específico del dominio.

1. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

2. En **tipos de proyecto**, expanda el nodo **otros tipos de proyectos** y haga clic en **extensibilidad**.

3. Haga clic en **Diseñador de lenguaje específico de dominio**.

     ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

4. En el cuadro **nombre** , escriba **familytree**. Haga clic en **OK**.

     Se abre el **Asistente para lenguaje específico de dominio** y muestra una lista de las soluciones DSL de plantilla.

     Haga clic en cada plantilla para ver una descripción.

     Las plantillas son puntos de partida útiles. Cada una de ellas proporciona un DSL de trabajo completo que puede editar para satisfacer sus necesidades. Normalmente, elegiría la plantilla más cercana a lo que desea crear.

5. Para este tutorial, elija la plantilla de **idioma mínima** .

6. Escriba una extensión de nombre de archivo para su DSL en la página del asistente correspondiente. Esta es la extensión que usarán los archivos que contienen instancias de su DSL.

    - Elija una extensión que no esté asociada a ninguna aplicación del equipo o en cualquier equipo en el que desee instalar el DSL. Por ejemplo, **docx** y **htm** serían extensiones de nombre de archivo no aceptables.

    - El asistente le advertirá en caso de que la extensión que haya especificado se esté usando como un DSL. Piense en usar una extensión de nombre de archivo diferente. También puede restablecer la instancia de Visual Studio SDK Experimental para borrar antiguos diseñadores experimentales. Haga clic en **Inicio**, **todos los programas**, **Microsoft Visual Studio SDK de 2010**, **herramientas**y, a continuación, **restablezca la instancia experimental de Microsoft Visual Studio 2010**.

7. Inspeccione las demás páginas y, a continuación, haga clic en **Finalizar**.

     Se genera una solución que contiene dos proyectos. Se denominan DSL y DslPackage. Se abre un archivo de diagrama denominado DslDefinition. DSL.

    > [!NOTE]
    > La mayor parte del código que se puede ver en las carpetas de los dos proyectos se genera a partir de DslDefinition. DSL. Por esta razón, la mayoría de las modificaciones en el DSL se realizan en este archivo.

Ahora, la interfaz de usuario es similar a la imagen siguiente.

![diseñador dsl](../modeling/media/dsl_designer.png)

Esta solución define un lenguaje específico de dominio. Para obtener más información, vea [información general sobre la interfaz de usuario de herramientas del lenguaje específico de dominio](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Partes importantes de la solución DSL

Tenga en cuenta los siguientes aspectos de la nueva solución:

- **Dsl\DslDefinition.DSL** Este es el archivo que se ve cuando se crea una solución DSL. La mayoría del código de la solución se genera a partir de este archivo, y la mayoría de los cambios que se realizan en una definición de DSL se realizan aquí. Para obtener más información, vea el apartado sobre cómo trabajar con el diagrama de la [definición de DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Proyecto DSL** Este proyecto contiene código que define el lenguaje específico del dominio.

- **Proyecto DslPackage** Este proyecto contiene código que permite abrir y editar instancias de DSL en Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Ejecutar el DSL

Puede ejecutar la solución DSL en cuanto la cree. Posteriormente, puede modificar la definición de DSL gradualmente y ejecutar la solución de nuevo después de cada cambio.

### <a name="to-experiment-with-the-dsl"></a>Para experimentar con el DSL

1. Haga clic en **transformar todas las plantillas** en la barra de herramientas **Explorador de soluciones** . Esto regenera la mayor parte del código fuente de DslDefinition. DSL.

    > [!NOTE]
    > Siempre que cambie *DslDefinition. DSL*, debe hacer clic en **transformar todas las plantillas** antes de recompilar la solución. Este paso se puede automatizar. Para obtener más información, consulte [cómo automatizar la transformación de todas las plantillas](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Presione **F5**o bien, en el menú **Depurar** , haga clic en **Iniciar depuración**.

     El DSL se compila y se instala en la instancia experimental de Visual Studio.

     Se inicia una instancia experimental de Visual Studio. La instancia experimental toma su configuración de un subárbol independiente del registro, donde las extensiones de Visual Studio se registran con fines de depuración. Las instancias normales de Visual Studio no tienen acceso a las extensiones registradas en ella.

3. En la instancia experimental de Visual Studio, abra el archivo de modelo denominado **Test** desde **Explorador de soluciones**.

     \- o -

     Haga clic con el botón secundario en el proyecto de depuración, elija **Agregar**y, a continuación, haga clic en **elemento**. En el cuadro de diálogo **Agregar elemento** , seleccione el tipo de archivo de su DSL.

     El archivo de modelo se abre como un diagrama en blanco.

     El cuadro de herramientas se abre y muestra las herramientas apropiadas para el tipo de diagrama.

4. Use las herramientas de para crear formas y conectores en el diagrama.

    1. Para crear formas, arrastre desde el herramienta Forma de ejemplo hasta el diagrama.

    2. Para conectar dos formas, haga clic en la herramienta conector de ejemplo, haga clic en la primera forma y, a continuación, haga clic en la segunda forma.

5. Haga clic en las etiquetas de las formas para cambiarlas.

El Visual Studio experimental se parecerá al ejemplo siguiente:

![Árbol de ejemplo de lenguaje específico de dominio en Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>El contenido de un modelo

El contenido de un archivo que es una instancia de DSL se denomina *modelo*. El modelo contiene los <em>elementos</em> del *modelo* y los *vínculos* entre los elementos. La definición de DSL especifica qué tipos de elementos de modelo y vínculos pueden existir en el modelo. Por ejemplo, en un DSL creado a partir de la plantilla de lenguaje mínima, hay un tipo de elemento de modelo y un tipo de vínculo.

La definición de DSL puede especificar cómo aparece el modelo en un diagrama. Puede elegir entre diversos estilos de formas y conectores. Puede especificar que algunas formas aparezcan dentro de otras formas.

Puede ver un modelo como un árbol en la vista del **Explorador** mientras edita un modelo. A medida que se agregan formas al diagrama, los elementos del modelo también aparecen en el explorador. Se puede usar el explorador aunque no haya ningún diagrama.

Si no puede ver el explorador en la instancia de depuración de Visual Studio, en el menú **Ver** , seleccione **otras ventanas**y, a continuación, haga clic en *\<Your Language>* **Explorador**.

### <a name="the-api-of-your-dsl"></a>La API de su DSL

El DSL genera una API que le permite leer y actualizar modelos que son instancias de DSL. Una aplicación de la API es generar archivos de texto a partir de un modelo. Para obtener más información, vea [generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

En la solución de depuración, abra los archivos de plantilla con la extensión ". TT". En estos ejemplos se muestra cómo puede generar texto a partir de modelos y le permite probar la API de su DSL. Uno de los ejemplos está escrito en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , el otro en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

En cada archivo de plantilla se encuentra el archivo que genera. Expanda el archivo de plantilla en Explorador de soluciones y abra el archivo generado.

El archivo de plantilla contiene un pequeño segmento de código que enumera todos los elementos del modelo.

El archivo generado contiene el resultado.

Al cambiar un archivo de modelo, verá los cambios correspondientes en los archivos generados después de volver a generar los archivos.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Para volver a generar archivos de texto después de cambiar el archivo de modelo

1. En la instancia experimental de Visual Studio, guarde el archivo de modelo.

2. Asegúrese de que el parámetro de nombre de archivo de cada archivo. TT hace referencia al archivo de modelo que está usando para los experimentos. Guarde el archivo. TT.

3. Haga clic en **transformar todas las plantillas** en la barra de herramientas de **Explorador de soluciones**.

     \- o -

     Haga clic con el botón secundario en las plantillas que desee regenerar y, a continuación, haga clic en **Ejecutar herramienta personalizada**.

Puede agregar cualquier número de archivos de plantilla de texto a un proyecto. Cada plantilla genera un archivo de resultados.

> [!NOTE]
> Cuando cambie la definición de DSL, el código de la plantilla de texto de ejemplo no funcionará, a menos que lo actualice.

Para obtener más información, vea [generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md) y [escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Personalizar el DSL

Si desea modificar la definición de DSL, cierre la instancia experimental y actualice la definición en la instancia principal de Visual Studio.

> [!NOTE]
> Una vez modificada la definición de DSL, podría perder información en los modelos de prueba creados con versiones anteriores.  Por ejemplo, la solución de depuración contiene un archivo denominado Sample, que contiene algunas formas y conectores. Después de empezar a desarrollar la definición de DSL, no estarán visibles y se perderán cuando guarde el archivo.

Puede crear una amplia variedad de extensiones para el DSL. Los ejemplos siguientes le darán una impresión de las posibilidades.

Después de cada cambio, guarde la definición de DSL, haga clic en **transformar todas las plantillas** en **Explorador de soluciones**y, a continuación, presione **F5** para experimentar con el DSL cambiado.

### <a name="rename-the-types-and-tools"></a>Cambiar el nombre de los tipos y las herramientas

Cambiar el nombre de las clases de dominio y las relaciones existentes. Por ejemplo, a partir de una definición de DSL creada a partir de la plantilla de idioma mínima, puede realizar las siguientes operaciones de cambio de nombre para que el DSL represente árboles de familia.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Para cambiar el nombre de las clases de dominio, las relaciones y las herramientas

1. En el diagrama DslDefinition, cambie el nombre de **ExampleModel** a **FamilyTreeModel**, **ExampleElement** a **Person**, **destinos** a **elementos primarios**y **orígenes** a **elementos secundarios**. Puede hacer clic en cada etiqueta para cambiarla.

     ![Diagrama de definición de DSL &#45; modelo de árbol de familia](../modeling/media/familyt_person.png)

2. Cambie el nombre del elemento y de las herramientas del conector.

    1. Abra la ventana Explorador de DSL haciendo clic en la ficha situada debajo de Explorador de soluciones. Si no lo ve, en el menú **Ver** , seleccione **otras ventanas** y, a continuación, haga clic en **Explorador de DSL**. DSL Explorer solo es visible cuando el diagrama de definición de DSL es la ventana activa.

    2. Abra el ventana Propiedades y colóquelo para poder ver las propiedades y el explorador de DSL al mismo tiempo.

    3. En el explorador de DSL, expanda **Editor**, **pestañas del cuadro de herramientas**, *\<your DSL>* y, a continuación, **herramientas**.

    4. Haga clic en **ExampleElement**. Este es el elemento del cuadro de herramientas que se usa para crear elementos.

    5. En el ventana Propiedades, cambie la propiedad **nombre** a **persona**.

         Observe que la propiedad **Caption** también cambia.

    6. Del mismo modo, cambie el nombre de la herramienta **ExampleConnector** a **ParentLink**. Modifique la propiedad **Caption** para que no sea una copia de la propiedad Name. Por ejemplo, escriba **vínculo primario**.

3. Vuelva a generar el DSL.

    1. Guarde el archivo de definición de DSL.

    2. Haga clic en **transformar todas las plantillas** en la barra de herramientas de explorador de soluciones

    3. Presione F5. Espere hasta que aparezca la instancia experimental de Visual Studio.

4. En la solución de depuración en la instancia experimental de Visual Studio, abra un archivo de modelo de prueba. Arrastre los elementos a él desde el cuadro de herramientas. Observe que los títulos de herramienta y los nombres de tipo en DSL Explorer han cambiado.

5. Guarde el archivo de modelo.

6. Abra un archivo. TT y reemplace las apariciones del tipo y los nombres de propiedad anteriores por los nuevos nombres.

7. Asegúrese de que el nombre de archivo que se especifica en el archivo. TT especifica el modelo de prueba.

8. Guarde el archivo. TT. Abra el archivo generado para ver el resultado de la ejecución del código en el archivo. TT. Compruebe que es correcta.

### <a name="add-domain-properties-to-classes"></a>Agregar propiedades de dominio a clases
 Agregue propiedades a una clase de dominio, por ejemplo, para representar los años de nacimiento y muerte de una persona.

 Para que las nuevas propiedades estén visibles en el diagrama, debe agregar elementos *Decorator* a la forma que muestra el elemento de modelo. También debe asignar las propiedades a los elementos Decorator.

##### <a name="to-add-properties-and-display-them"></a>Para agregar propiedades y mostrarlas

1. Agregue las propiedades.

   1. En el diagrama de definición de DSL, haga clic con el botón secundario en la clase de dominio **Person** , seleccione **Agregar**y, a continuación, haga clic en **propiedad de dominio**.

   2. Escriba una lista de nuevos nombres de propiedad, como **nacimiento** y **muerte**. Presione **entrar** después de cada uno de ellos.

2. Agregue elementos Decorator que mostrarán las propiedades de la forma.

   1. Siga la línea gris que se extiende desde la clase de dominio person al otro lado del diagrama. Se trata de una asignación de elemento de diagrama. Vincula la clase de dominio a una clase de forma.

   2. Haga clic con el botón secundario en esta clase de forma, seleccione **Agregar**y, a continuación, haga clic en **Decorator de texto**.

   3. Agregue dos elementos Decorator con nombres como **BirthDecorator** y **DeathDecorator**.

   4. Seleccione cada nuevo elemento Decorator y, en el ventana Propiedades, establezca el campo **posición** . Esto determina dónde se mostrará el valor de la propiedad de dominio en la forma. Por ejemplo, establezca **InnerBottomLeft** y **InnerBottomRight**.

        ![Definición de forma de compartimiento](../modeling/media/familyt_compartment.png)

3. Asigne los elementos Decorator a las propiedades.

   1. Abra la ventana DSL Details (Detalles de DSL). Normalmente, se encuentra en una pestaña junto a la ventana de salida. Si no lo ve, en el menú **Ver** , seleccione **otras ventanas**y, a continuación, haga clic en **detalles de DSL**.

   2. En el diagrama de definición de DSL, haga clic en la línea que conecta la clase de dominio **Person** con la clase Shape.

   3. En **detalles de DSL**, en la pestaña **asignaciones de Decorator** , haga clic en la casilla de un elemento Decorator sin asignar. En la **propiedad Mostrar**, seleccione la propiedad de dominio a la que desea asignarla. Por ejemplo, asigne **BirthDecorator** a **Birth**.

4. Guarde el DSL, haga clic en transformar todas las plantillas y presione F5.

5. En un diagrama de modelo de ejemplo, compruebe que ahora puede hacer clic en las posiciones que eligió y escribir valores en ellas. Además, al seleccionar una forma **persona** , el ventana Propiedades muestra las nuevas propiedades nacimiento y muerte.

6. En un archivo. TT, puede agregar código que obtenga las propiedades de cada persona.

   ![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definir clases nuevas
 Puede Agregar clases de dominio y relaciones a un modelo. Por ejemplo, podría crear una nueva clase para representar ciudades y una nueva relación para representar que una persona ha vivido en una ciudad.

 Para que los distintos tipos sean distintos en un diagrama del modelo, puede asignar las clases de dominio a distintos tipos de formas o a formas con diferentes colores y geometría.

##### <a name="to-add-and-display-a-new-domain-class"></a>Para agregar y mostrar una nueva clase de dominio

1. Agregue una clase de dominio y conviértalo en un elemento secundario de la raíz del modelo.

    1. En el diagrama de definición de DSL, haga clic en la herramienta **incrustar relación** , haga clic en la clase raíz **FamilyTreeModel**y, a continuación, haga clic en una parte vacía del diagrama.

         Aparece una nueva clase de dominio que está conectada a FamilyTreeModel con una relación de incrustación.

         Establezca su nombre, por ejemplo, **ciudad**.

        > [!NOTE]
        > Cada clase de dominio, excepto la raíz del modelo, debe ser el destino de al menos una relación de incrustación, o debe heredar de una clase que sea el destino de una inserción. Por esta razón, a menudo es conveniente crear una clase de dominio mediante la herramienta de relación de incrustación.

    2. Agregue una propiedad de dominio a la nueva clase, por ejemplo **nombre**.

2. Agregue una relación de referencia entre persona y ciudad.

    1. Haga clic en la herramienta **relación de referencia** , haga clic en persona y, a continuación, en ciudad.

         ![Fragmento de definición DSL: raíz de árbol genealógico](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Las relaciones de referencia representan referencias cruzadas de una parte del árbol del modelo a otra.

3. Agregue una forma para representar ciudades en los diagramas del modelo.

    1. Arrastre una **forma de geometría** desde el cuadro de herramientas al diagrama y cambie su nombre, por ejemplo **TownShape**.

    2. En el ventana Propiedades, establezca los campos de apariencia de la nueva forma, como color de relleno y geometría.

    3. Agregue un elemento Decorator para mostrar el nombre de la ciudad y asígnele el nombre NameDecorator. Establezca su propiedad posición.

4. Asigne la clase de dominio ciudad a TownShape.

    1. Haga clic en la herramienta **mapa de elementos de diagrama** , haga clic en la clase de dominio ciudad y, a continuación, en la clase de forma TownShape.

    2. En la pestaña asignaciones de elemento **Decorator** de la ventana **detalles de DSL** con el conector de mapas seleccionado, Active NameDecorator y establezca la **propiedad display** en Name.

5. Cree un conector para mostrar la relación entre person y ciudades.

    1. Arrastre un conector desde el cuadro de herramientas hasta el diagrama. Cambie su nombre y establezca sus propiedades de apariencia.

    2. Use la herramienta de **asignación de elementos de diagrama** para vincular el nuevo conector a la relación entre persona y ciudad.

         ![Definición de árbol genealógico con asignación de forma agregada](../modeling/media/familyt_shapemap.png)

6. Cree una herramienta de elemento para crear una nueva ciudad.

    1. En **DSL Explorer**, expanda **Editor** y, a continuación, **pestañas del cuadro de herramientas**.

    2. Haga clic con el botón secundario *\<your DSL>* y después haga clic en **Agregar nuevo elemento herramienta**.

    3. Establezca la propiedad **nombre** de la nueva herramienta y establezca su propiedad **clase** en ciudad.

    4. Establezca la propiedad **icono del cuadro de herramientas** . Haga clic en **[...]** y, en el campo **nombre de archivo** , seleccione un archivo de icono.

7. Cree una herramienta de conector para crear un vínculo entre ciudades y People.

    1. Haga clic con el botón secundario *\<your DSL>* y, a continuación, haga clic en **Agregar nueva herramienta de conector**.

    2. Establezca la propiedad nombre de la nueva herramienta.

    3. En la propiedad **ConnectionBuilder** , seleccione el generador que contiene el nombre de la relación persona-ciudad.

    4. Establezca el **icono del cuadro de herramientas**.

8. Guarde la definición de DSL, haga clic en **transformar todas las plantillas**y, a continuación, presione **F5**.

9. En la instancia experimental de Visual Studio, abra un archivo de modelo de prueba. Use las nuevas herramientas para crear ciudades y vínculos entre ciudades y persons. Tenga en cuenta que solo puede crear vínculos entre los tipos de elemento correctos.

10. Cree código que muestre la ciudad en la que vive cada persona. Las plantillas de texto son una de las ubicaciones donde puede ejecutar este código. Por ejemplo, puede modificar el archivo Sample.tt existente en la solución de depuración para que contenga el código siguiente:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     Al guardar el archivo *. TT, se creará un archivo subsidiario que contiene la lista de personas y sus residencias. Para obtener más información, vea [generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Validación y comandos
 También podría desarrollar este DSL agregando restricciones de validación. Estas restricciones son métodos que se pueden definir, que se aseguran de que el modelo se encuentre en un estado correcto. Por ejemplo, puede definir una restricción para asegurarse de que la fecha de nacimiento de un elemento secundario es posterior a la de sus elementos primarios. La característica de validación muestra una advertencia si el usuario de DSL intenta guardar un modelo que interrumpe cualquiera de las restricciones. Para obtener más información, vea [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).

 También puede definir comandos de menú que el usuario puede invocar. Los comandos pueden modificar el modelo. También pueden interactuar con otros modelos en Visual Studio y con recursos externos. Para obtener más información, vea [Cómo: modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Implementación de DSL
 Para permitir a otros usuarios usar el lenguaje específico de dominio, distribuya un archivo de extensión de Visual Studio (VSIX). Esto se crea al compilar la solución DSL.

 Busque el archivo. vsix en la carpeta bin de la solución. Cópielo en el equipo en el que desea instalarlo. En ese equipo, haga doble clic en el archivo VSIX. El DSL puede usarse en todas las instancias de Visual Studio en ese equipo.

 Puede usar el mismo procedimiento para instalar el DSL en su propio equipo, de modo que no tenga que usar la instancia experimental de Visual Studio.

 Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Quitar DSL experimentales anteriores
 Si ha creado DSL experimentales que ya no desea, puede quitarlos del equipo restableciendo la instancia experimental de Visual Studio.

 Esto quitará del equipo todos los DSL experimentales y otras extensiones experimentales de Visual Studio. Se trata de extensiones que se han ejecutado en modo de depuración.

 Este procedimiento no quita los DSL ni otras extensiones de Visual Studio que se han instalado por completo ejecutando el archivo VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Para restablecer la instancia experimental de Visual Studio

1. Haga clic en **Inicio**, **todos los programas**, **Microsoft Visual Studio SDK de 2010**, **herramientas**y, a continuación, **restablezca la instancia experimental de Microsoft Visual Studio 2010**.

2. Vuelva a compilar cualquier DSL experimental u otras extensiones experimentales de Visual Studio que desee usar.

## <a name="see-also"></a>Consulte también

- [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
