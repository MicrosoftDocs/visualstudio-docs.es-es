---
title: Introducción a los lenguajes específicos de dominio
description: Obtenga información sobre los conceptos básicos para definir y usar un lenguaje específico de dominio (DSL) creado con el SDK de modelado para Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2637703e068a98e20f209d5de51a6003a4dd7f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386740"
---
# <a name="get-started-with-domain-specific-languages"></a>Introducción a los lenguajes específicos de dominio

En este tema se explican los conceptos básicos para definir y usar un lenguaje específico de dominio (DSL) creado con el SDK de modelado para Visual Studio.

> [!NOTE]
> El SDK de transformación Plantilla de texto y el SDK Visual Studio Modeling se instalan automáticamente al instalar características específicas de Visual Studio. Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/) para obtener más información.

Si no está nuevo en las DSL, se recomienda que trabaje en el laboratorio de herramientas dsl, que puede encontrar en este sitio: SDK de visualización [y modelado.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>¿Qué puede hacer con un Domain-Specific language?

Un lenguaje específico del dominio es una notación, normalmente gráfica, que está diseñada para usarse para un propósito determinado. Por el contrario, los lenguajes como UML son de uso general. En un DSL, puede definir los tipos de elemento de modelo y sus relaciones, y cómo se presentan en la pantalla.

Cuando haya diseñado un DSL, puede distribuirlo como parte de un paquete Visual Studio Integration Extension (VSIX). Los usuarios trabajan con el DSL en Visual Studio:

![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt_instance.png)

La notación solo forma parte de un DSL. Junto con la notación, el paquete VSIX incluye herramientas que los usuarios pueden aplicar para ayudarles a editar y generar material a partir de sus modelos.

Una de las aplicaciones principales de las DSL es generar código de programa, archivos de configuración y otros artefactos. Especialmente en proyectos de gran tamaño y líneas de producto, donde se crearán varias variantes de un producto, la generación de muchos de los aspectos variables de las DSL puede proporcionar un gran aumento en la confiabilidad y una respuesta muy rápida a los cambios de requisitos.

El resto de esta información general es un tutorial que presenta las operaciones básicas de creación y uso de un lenguaje específico de dominio en Visual Studio.

## <a name="prerequisites"></a>Requisitos previos

Para definir un DSL, debe tener instalados los siguientes componentes:

| Componente | Vínculo |
|-|-|
| Programa para la mejora | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| SDK de modelado para Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Creación de una solución DSL

Para crear un nuevo lenguaje específico de dominio, cree una nueva solución Visual Studio mediante la plantilla de proyecto Domain-Specific Language.

1. En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.

2. En **Tipos de proyecto**, expanda el nodo Otros tipos **de** proyecto y haga clic **en Extensibilidad**.

3. Haga **clic Diseñador de lenguaje específico de dominio**.

     ![Cuadro de diálogo para crear solución DSL](../modeling/media/create_dsldialog.png)

4. En el **cuadro** Nombre, escriba **FamilyTree**. Haga clic en **Aceptar**.

     Se **abre el Asistente para lenguaje específico de dominio** y se muestra una lista de soluciones DSL de plantilla.

     Haga clic en cada plantilla para ver una descripción.

     Las plantillas son puntos de partida útiles. Cada una de ellas proporciona un DSL de trabajo completo, que puede editar para satisfacer sus necesidades. Normalmente, elegiría la plantilla más cercana a la que desea crear.

5. Para este tutorial, elija la **plantilla Lenguaje** mínimo.

6. Escriba una extensión de nombre de archivo para su DSL en la página del asistente correspondiente. Esta es la extensión que usarán los archivos que contienen instancias de su DSL.

    - Elija una extensión que no esté asociada a ninguna aplicación del equipo o en cualquier equipo en el que desee instalar el DSL. Por ejemplo, **docx** y **htm** serían extensiones de nombre de archivo inaceptables.

    - El asistente le advertirá en caso de que la extensión que haya especificado se esté usando como un DSL. Piense en usar una extensión de nombre de archivo diferente. También puede restablecer la instancia de Visual Studio SDK Experimental para borrar antiguos diseñadores experimentales. Haga clic  **en** Inicio , haga clic en Todos los programas , Microsoft Visual Studio SDK **de 2010** **,** Herramientas y, a continuación, restablezca la instancia experimental de **Microsoft Visual Studio 2010**.

7. Inspeccione las demás páginas y, a continuación, haga clic **en Finalizar.**

     Se genera una solución que contiene dos proyectos. Se denominan Dsl y DslPackage. Se abre un archivo de diagrama denominado DslDefinition.dsl.

    > [!NOTE]
    > La mayor parte del código que puede ver en las carpetas de los dos proyectos se genera a partir de DslDefinition.dsl. Por este motivo, la mayoría de las modificaciones en el DSL se realizan en este archivo.

Ahora, la interfaz de usuario es similar a la imagen siguiente.

![diseñador dsl](../modeling/media/dsl_designer.png)

Esta solución define un lenguaje específico de dominio. Para obtener más información, vea [Información general de Domain-Specific Language Tools Interfaz de usuario](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Las partes importantes de la solución DSL

Observe los siguientes aspectos de la nueva solución:

- **Dsl\DslDefinition.dsl** Este es el archivo que se ve al crear una solución DSL. Casi todo el código de la solución se genera a partir de este archivo y la mayoría de los cambios que se realizan en una definición de DSL se realizan aquí. Para obtener más información, vea Trabajar con el [diagrama de definición de DSL.](../modeling/working-with-the-dsl-definition-diagram.md)

- **Proyecto dsl** Este proyecto contiene código que define el lenguaje específico del dominio.

- **Proyecto DslPackage** Este proyecto contiene código que permite abrir y editar instancias del DSL en Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Ejecución del DSL

Puede ejecutar la solución DSL en cuanto la haya creado. Más adelante, puede modificar la definición de DSL gradualmente, ejecutando de nuevo la solución después de cada cambio.

### <a name="to-experiment-with-the-dsl"></a>Para experimentar con el DSL

1. Haga **clic en Transformar todas las** plantillas en la barra **Explorador de soluciones** herramientas. Esto vuelve a generar la mayor parte del código fuente de DslDefinition.dsl.

    > [!NOTE]
    > Siempre que cambie *DslDefinition.dsl,* debe hacer clic en **Transformar todas las plantillas** antes de volver a generar la solución. Este paso se puede automatizar. Para obtener más información, [vea How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Presione **F5** o bien, en el menú **Depurar** , haga clic en **Iniciar depuración**.

     El DSL se compila y se instala en la instancia experimental de Visual Studio.

     Una instancia experimental de Visual Studio inicia. La instancia experimental toma su configuración de un subárbol independiente del registro, donde las extensiones Visual Studio se registran con fines de depuración. Las instancias normales Visual Studio no tienen acceso a las extensiones registradas allí.

3. En la instancia experimental de Visual Studio, abra el archivo de modelo denominado **Test** **desde Explorador de soluciones**.

     \- O bien

     Haga clic con el botón derecho en el proyecto Depuración, **seleccione Agregar** y, a continuación, haga clic en **Elemento**. En el **cuadro de diálogo Agregar** elemento, seleccione el tipo de archivo del DSL.

     El archivo de modelo se abre como un diagrama en blanco.

     El cuadro de herramientas se abre y muestra las herramientas adecuadas para el tipo de diagrama.

4. Use las herramientas para crear formas y conectores en el diagrama.

    1. Para crear formas, arrastre desde el cuadro de herramienta Forma al diagrama.

    2. Para conectar dos formas, haga clic en la herramienta Conector de ejemplo, haga clic en la primera forma y, a continuación, haga clic en la segunda forma.

5. Haga clic en las etiquetas de las formas para cambiarlas.

El Visual Studio experimental será similar al ejemplo siguiente:

![Árbol de ejemplo de lenguaje específico del dominio en Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>El contenido de un modelo

El contenido de un archivo que es una instancia de un DSL se denomina *modelo*. El modelo contiene *elementos de* <em>modelo</em> y *vínculos* entre los elementos . La definición de DSL especifica qué tipos de elementos y vínculos del modelo pueden existir en el modelo. Por ejemplo, en un DSL creado a partir de la plantilla Lenguaje mínimo, hay un tipo de elemento de modelo y un tipo de vínculo.

La definición de DSL puede especificar cómo aparece el modelo en un diagrama. Puede elegir entre una variedad de estilos de formas y conectores. Puede especificar que algunas formas aparezcan dentro de otras formas.

Puede ver un modelo como un árbol en la **vista Explorador** mientras edita un modelo. A medida que agrega formas al diagrama, los elementos del modelo también aparecen en el explorador. El explorador se puede usar incluso si no hay ningún diagrama.

Si no puede ver el Explorador en la instancia de  depuración de Visual Studio, en el menú Ver , seleccione Otras **ventanas** y, a continuación, haga clic *\<Your Language>* **en Explorador**.

### <a name="the-api-of-your-dsl"></a>La API del DSL

El DSL genera una API que permite leer y actualizar modelos que son instancias del DSL. Una aplicación de la API es generar archivos de texto a partir de un modelo. Para obtener más información, vea [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

En la solución Depuración, abra los archivos de plantilla con la extensión ".tt". Estos ejemplos muestran cómo puede generar texto a partir de modelos y le permiten probar la API de su DSL. Uno de los ejemplos está escrito en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , el otro en [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

En cada archivo de plantilla se encuentra el archivo que genera. Expanda el archivo de plantilla Explorador de soluciones y abra el archivo generado.

El archivo de plantilla contiene un segmento corto de código que enumera todos los elementos del modelo.

El archivo generado contiene el resultado.

Al cambiar un archivo de modelo, verá los cambios correspondientes en los archivos generados después de volver a generar los archivos.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Para volver a generar archivos de texto después de cambiar el archivo de modelo

1. En la instancia experimental de Visual Studio, guarde el archivo de modelo.

2. Asegúrese de que el parámetro de nombre de archivo de cada archivo .tt hace referencia al archivo de modelo que usa para los experimentos. Guarde el archivo .tt.

3. Haga **clic en Transformar todas las** plantillas en la barra de herramientas **Explorador de soluciones**.

     \- O bien

     Haga clic con el botón derecho en las plantillas que desea volver a generar y, a continuación, haga clic **en Ejecutar herramienta personalizada**.

Puede agregar cualquier número de archivos de plantilla de texto a un proyecto. Cada plantilla genera un archivo de resultados.

> [!NOTE]
> Al cambiar la definición de DSL, el código de plantilla de texto de ejemplo no funcionará, a menos que lo actualice.

Para obtener más información, vea Generar código a partir de [un lenguaje Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md) y Escribir código para personalizar un Domain-Specific [personalizado.](../modeling/writing-code-to-customise-a-domain-specific-language.md)

## <a name="customizing-the-dsl"></a>Personalizar el DSL

Si desea modificar la definición de DSL, cierre la instancia experimental y actualice la definición en la instancia Visual Studio principal.

> [!NOTE]
> Después de modificar la definición de DSL, es posible que pierda información en los modelos de prueba que ha creado mediante versiones anteriores.  Por ejemplo, la solución de depuración contiene un archivo denominado Sample, que contiene algunas formas y conectores. Después de empezar a desarrollar la definición de DSL, no estarán visibles y se perderán al guardar el archivo.

Puede crear una amplia variedad de extensiones para su DSL. Los ejemplos siguientes le darán una impresión de las posibilidades.

Después de cada cambio, guarde  la definición de DSL, haga clic en Transformar todas las plantillas en Explorador de soluciones y, **a** continuación, presione **F5** para experimentar con el DSL cambiado.

### <a name="rename-the-types-and-tools"></a>Cambiar el nombre de tipos y herramientas

Cambie el nombre de las clases y relaciones de dominio existentes. Por ejemplo, a partir de una definición de Dsl creada a partir de la plantilla Lenguaje mínimo, puede realizar las siguientes operaciones de cambio de nombre para que el DSL represente árboles de familia.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Para cambiar el nombre de las clases, relaciones y herramientas de dominio

1. En el diagrama DslDefinition, cambie el nombre de **ExampleModel** a **FamilyTreeModel,** **ExampleElement** a **Person**, **Targets** to **Parents** y **Sources** to **Children**. Puede hacer clic en cada etiqueta para cambiarla.

     ![Diagrama de definición de DSL &#45; modelo de árbol de familia](../modeling/media/familyt_person.png)

2. Cambie el nombre del elemento y las herramientas del conector.

    1. Para abrir la ventana del Explorador dsl, haga clic en la pestaña Explorador de soluciones. Si no puede verlo,  en el menú Ver, seleccione **Otras ventanas** y, a continuación, haga clic en **Explorador dsl.** El Explorador de DSL solo es visible cuando el diagrama de definición de DSL es la ventana activa.

    2. Abra el ventana Propiedades y posiciones para que pueda ver el Explorador dsl y las propiedades al mismo tiempo.

    3. En el Explorador de DSL, expanda **Editor**, **Pestañas del cuadro de herramientas**, *\<your DSL>* y, a continuación, **Herramientas**.

    4. Haga clic **en ExampleElement**. Este es el elemento del cuadro de herramientas que se usa para crear elementos.

    5. En el ventana Propiedades, cambie la **propiedad Name** a **Person**.

         Observe que la **propiedad Caption** también cambia.

    6. De la misma manera, cambie el nombre de la **herramienta ExampleConnector** a **ParentLink**. Modifique la **propiedad Caption** para que no sea una copia de la propiedad Name. Por ejemplo, escriba **Vínculo primario**.

3. Recompile el DSL.

    1. Guarde el archivo de definición de DSL.

    2. Haga **clic en Transformar todas las** plantillas en la barra de herramientas de Explorador de soluciones

    3. Presione F5. Espere hasta que aparezca la instancia experimental Visual Studio.

4. En la solución Depuración de la instancia experimental de Visual Studio, abra un archivo de modelo de prueba. Arrastre elementos a él desde el cuadro de herramientas. Observe que los títulos de la herramienta y los nombres de tipo en el Explorador de DSL han cambiado.

5. Guarde el archivo de modelo.

6. Abra un archivo .tt y reemplace las apariciones de los nombres de tipo y propiedad antiguos por los nuevos nombres.

7. Asegúrese de que el nombre de archivo especificado en el archivo .tt especifica el modelo de prueba.

8. Guarde el archivo .tt. Abra el archivo generado para ver el resultado de ejecutar el código en el archivo .tt. Compruebe que es correcto.

### <a name="add-domain-properties-to-classes"></a>Agregar propiedades de dominio a clases
 Agregue propiedades a una clase de dominio, por ejemplo, para representar los años de nacimiento y muerte de una persona.

 Para que las nuevas propiedades sean visibles en el diagrama, debe agregar *elementos decorator* a la forma que muestra el elemento del modelo. También debe asignar las propiedades a los decoradores.

##### <a name="to-add-properties-and-display-them"></a>Para agregar propiedades y mostrarlas

1. Agregue las propiedades.

   1. En el diagrama de definición de DSL, haga clic con el botón derecho en la clase de dominio **Person,** seleccione **Agregar** y, a continuación, haga clic en **Propiedad de dominio**.

   2. Escriba una lista de nuevos nombres de propiedad, como **Nacimiento** y **muerte.** Presione **Entrar** después de cada uno de ellos.

2. Agregue elementos decorator que mostrarán las propiedades en la forma .

   1. Siga la línea gris que se extiende desde la clase de dominio Person al otro lado del diagrama. Se trata de un mapa de elementos de diagrama. Vincula la clase de dominio a una clase de forma.

   2. Haga clic con el botón derecho en esta clase de forma, **seleccione Agregar** y, a continuación, haga clic **en Decorador de texto.**

   3. Agregue dos decoradores con nombres como **BirthDecorator** y **DeathDecorator.**

   4. Seleccione cada nuevo decorador y, en la ventana Propiedades, establezca el **campo Posición.** Esto determina dónde se mostrará el valor de la propiedad de dominio en la forma. Por ejemplo, establezca **InnerBottomLeft** e **InnerBottomRight.**

        ![Definición de forma de compartimiento](../modeling/media/familyt_compartment.png)

3. Asigne los elementos decorator a las propiedades.

   1. Abra la ventana DSL Details (Detalles de DSL). Normalmente se encuentra en una pestaña junto a la ventana Salida. Si no puede verlo,  en el menú Ver, seleccione Otras **ventanas** y, a continuación, haga clic en **Detalles de DSL**.

   2. En el diagrama de definición de DSL, haga clic en la línea que conecta la clase de dominio **Person** a la clase de forma.

   3. En **Detalles de DSL**, en la pestaña **Asignaciones de** decorador, haga clic en la casilla de un decorador sin asignación. En **Mostrar propiedad**, seleccione la propiedad de dominio a la que desea asignarla. Por ejemplo, asigne **BirthDecorator** a **Birth**.

4. Guarde el DSL, haga clic en Transformar todas las plantillas y presione F5.

5. En un diagrama de modelo de ejemplo, compruebe que ahora puede hacer clic en las posiciones que eligió y escribir valores en ellas. Además, al seleccionar una forma **Persona,** el ventana Propiedades muestra las nuevas propiedades Nacimiento y Muerte.

6. En un archivo .tt, puede agregar código que obtenga las propiedades de cada persona.

   ![Diagrama de árbol genealógico, cuadro de herramientas y explorador](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definición de clases nuevas
 Puede agregar clases de dominio y relaciones a un modelo. Por ejemplo, podría crear una nueva clase para representar a los vecinos y una nueva relación para representar que una persona residía en una ciudad.

 Para que los distintos tipos se distinguien en un diagrama de modelos, puede asignar las clases de dominio a diferentes tipos de forma o a formas con diferentes geometrías y colores.

##### <a name="to-add-and-display-a-new-domain-class"></a>Para agregar y mostrar una nueva clase de dominio

1. Agregue una clase de dominio y conséctela como un elemento secundario de la raíz del modelo.

    1. En el diagrama de definición de DSL, haga clic en la herramienta **Relación** de inserción, haga clic en la clase raíz **FamilyTreeModel** y, a continuación, haga clic en una parte vacía del diagrama.

         Aparece una nueva clase de dominio que está conectada a FamilyTreeModel con una relación de inserción.

         Establezca su nombre, por ejemplo **Ciudad.**

        > [!NOTE]
        > Todas las clases de dominio excepto la raíz del modelo deben ser el destino de al menos una relación de inserción, o bien deben heredar de una clase que sea el destino de una inserción. Por este motivo, suele ser conveniente crear una clase de dominio mediante la herramienta Relación de inserción.

    2. Agregue una propiedad de dominio a la nueva clase, por ejemplo **Nombre**.

2. Agregue una relación de referencia entre Person y Town.

    1. Haga clic en la **herramienta Relación de** referencia, haga clic en Persona y, a continuación, en Ciudad.

         ![Fragmento de definición DSL: raíz de árbol genealógico](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Las relaciones de referencia representan referencias cruzadas de una parte del árbol de modelos a otra.

3. Agregue una forma para representar la zona en los diagramas del modelo.

    1. Arrastre una forma **de geometría** desde el cuadro de herramientas al diagrama y cámbiele el nombre, por **ejemplo, TownShape**.

    2. En la ventana Propiedades, establezca los campos Apariencia de la nueva forma, como Color de relleno y Geometría.

    3. Agregue un elemento Decorator para mostrar el nombre de la ciudad y cámbiele el nombre NameDecorator. Establezca su propiedad Position.

4. Asigne la clase de dominio Ciudad a la forma de ciudad.

    1. Haga clic en **la herramienta Mapa de elementos** de diagrama, haga clic en la clase de dominio Ciudad y, a continuación, en la clase de forma TownShape.

    2. En la **pestaña Decorator Maps (Mapas** de decorador) de la ventana DSL Details (Detalles de **DSL)** con el conector de mapa seleccionado, active NameDecorator y establezca Display Property (Mostrar **propiedad)** en Name (Nombre).

5. Cree un conector para mostrar la relación entre Persona y Vecinos.

    1. Arrastre un conector desde el cuadro de herramientas al diagrama. Cámbiele el nombre y establezca sus propiedades de apariencia.

    2. Use la **herramienta Mapa de elementos** de diagrama para vincular el nuevo conector a la relación entre Person y Town.

         ![Definición de árbol genealógico con asignación de forma agregada](../modeling/media/familyt_shapemap.png)

6. Cree una herramienta de elemento para crear una nueva ciudad.

    1. En el **Explorador de DSL,** expanda **Editor y,** a continuación, **Pestañas del cuadro de herramientas**.

    2. Haga clic con el botón *\<your DSL>* derecho y, a continuación, **haga clic en Agregar nueva herramienta de elemento**.

    3. Establezca la **propiedad Name** de la nueva herramienta y establezca su **propiedad Class** en Ciudad.

    4. Establezca la propiedad **Icono del cuadro de** herramientas. Haga **clic en [...]** y, en el campo Nombre **de** archivo, seleccione un archivo de icono.

7. Cree una herramienta de conector para crear un vínculo entre los vecinos y las personas.

    1. Haga clic con el botón *\<your DSL>* derecho y, a continuación, **haga clic en Agregar nueva herramienta de conector**.

    2. Establezca la propiedad Nombre de la nueva herramienta.

    3. En la **propiedad ConnectionBuilder,** seleccione el generador que contiene el nombre del Person-Town relación.

    4. Establezca el icono **del cuadro de herramientas**.

8. Guarde la definición de DSL, haga clic **en Transformar todas las plantillas** y, a continuación, presione **F5**.

9. En la instancia experimental de Visual Studio, abra un archivo de modelo de prueba. Use las nuevas herramientas para crear vecinos y vínculos entre las personas y las personas. Tenga en cuenta que solo puede crear vínculos entre los tipos correctos de elemento.

10. Cree código que enumera la ciudad en la que reside cada persona. Las plantillas de texto son uno de los lugares donde se puede ejecutar este código. Por ejemplo, puede modificar el archivo de Sample.tt existente en la solución de depuración para que contenga el código siguiente:

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

     Al guardar el archivo *.tt, se creará un archivo subsidiaria que contiene la lista de personas y sus residencias. Para obtener más información, vea [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Validación y comandos
 Puede desarrollar aún más este DSL agregando restricciones de validación. Estas restricciones son métodos que se pueden definir y que se asegura de que el modelo está en un estado correcto. Por ejemplo, podría definir una restricción para asegurarse de que la fecha de nacimiento de un menor sea posterior a la de sus padres. La característica de validación muestra una advertencia si el usuario dsl intenta guardar un modelo que interrumpe cualquiera de las restricciones. Para obtener más información, [vea Validación en un Domain-Specific lenguaje .](../modeling/validation-in-a-domain-specific-language.md)

 También puede definir comandos de menú que el usuario puede invocar. Los comandos pueden modificar el modelo. También pueden interactuar con otros modelos en Visual Studio y con recursos externos. Para obtener más información, [vea Cómo: Modificar un comando de menú estándar](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Implementación del DSL
 Para permitir que otros usuarios usen el lenguaje específico del dominio, distribuya un archivo Visual Studio extensión (VSIX). Esto se crea al compilar la solución DSL.

 Busque el archivo .vsix en la carpeta bin de la solución. Cópielo en el equipo en el que desea instalarlo. En ese equipo, haga doble clic en el archivo VSIX. El DSL se puede usar en todas las instancias de Visual Studio en ese equipo.

 Puede usar el mismo procedimiento para instalar el DSL en su propio equipo para que no tenga que usar la instancia experimental de Visual Studio.

 Para obtener más información, vea [Implementación de soluciones de lenguaje específico de dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Eliminación de archivos DSL experimentales antiguos
 Si ha creado archivos DSL experimentales que ya no desea, puede quitarlos del equipo mediante el restablecimiento de la Visual Studio experimental.

 Esto quitará del equipo todas las DSL experimentales y otras extensiones Visual Studio experimentales. Se trata de extensiones que se han ejecutado en modo de depuración.

 Este procedimiento no quita las DSL u otras extensiones Visual Studio que se han instalado completamente mediante la ejecución del archivo VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Para restablecer la Visual Studio experimental

1. Haga clic  **en** Inicio , haga clic en Todos los programas , Microsoft Visual Studio SDK **de 2010** **,** Herramientas y, a continuación, restablezca la instancia experimental de **Microsoft Visual Studio 2010**.

2. Recompile las DSL experimentales u otras extensiones Visual Studio experimentales que todavía desee usar.

## <a name="see-also"></a>Vea también

- [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
