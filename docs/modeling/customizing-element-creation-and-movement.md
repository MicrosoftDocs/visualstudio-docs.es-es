---
title: Personalizar la creación y el movimiento de los elementos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: e56688d74647c12340fcf9755dca3de282806773
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933031"
---
# <a name="customizing-element-creation-and-movement"></a>Personalizar la creación y el movimiento de los elementos

Puede permitir que un elemento se arrastra hasta otro, desde el cuadro de herramientas o en una operación de pegado o mover la operación. Puede tener los elementos movidos vinculados a los elementos de destino, el uso de las relaciones que especifique.

Una directiva de fusión mediante combinación de elementos (EMD) especifica lo que ocurre cuando un elemento de modelo es *combinada* en otro elemento de modelo. Esto sucede cuando:

- El usuario arrastra desde el cuadro de herramientas hasta el diagrama o una forma.

- El usuario crea un elemento mediante el uso de un menú Agregar en el explorador o una forma de compartimiento.

- El usuario mueve un elemento de una calle a otra.

- El usuario pega un elemento.

- El código del programa llama a la directiva de combinación del elemento.

Aunque pueden parecer las operaciones de creación sea distinto de las operaciones de copia, trabajan realmente en la misma manera. Cuando se agrega un elemento, por ejemplo en el cuadro de herramientas, un prototipo de la se replica. El prototipo se combina con el modelo en la misma manera que los elementos que se han copiado desde otra parte del modelo.

La responsabilidad de una EMD es decidir cómo se debe combinar un objeto o grupo de objetos en una ubicación determinada en el modelo. En concreto, decide qué relaciones deben crearse para vincular el grupo combinado en el modelo. También puede personalizar para establecer las propiedades y para crear objetos adicionales.

![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png)

Una EMD se genera automáticamente al definir una relación de incrustación. Este valor predeterminado EMD crea una instancia de la relación cuando los usuarios agreguen nuevas instancias de elemento secundario al elemento primario. Puede modificar estos EMDs de forma predeterminada, por ejemplo agregando código personalizado.

También puede agregar sus propios EMDs en la definición de DSL, para permitir que los usuarios arrastrar o pegar diferentes combinaciones de clases de recepción y combinadas.

## <a name="defining-an-element-merge-directive"></a>Definir una directiva de fusión mediante combinación de elementos

Puede agregar directivas de combinación de elementos a las clases de dominio, relaciones de dominio, formas, conectores y diagramas. Puede agregar o encontrarlas en el Explorador de DSL en la clase de dominio receptora. La clase receptora es la clase de dominio del elemento que ya está en el modelo y en la que se van a combinar el elemento nuevo o copiar.

![DSL&#45;EMD&#95;detalles](../modeling/media/dsl-emd_details.png)

El **indización clase** es la clase de dominio de los elementos que se pueden mezclar con los miembros de la clase receptora. Las instancias de subclases de la clase de indización se combinarán también por esta EMD, a menos que establezca **se aplica a las subclases** en False.

Hay dos tipos de directiva de combinación:

- Un **proceso de mezcla** directiva especifica las relaciones que se debe vincular el nuevo elemento en el árbol.

- Un **reenviar mezcla** directiva redirige el nuevo elemento a otro elemento de recepción, normalmente un elemento primario.

Puede agregar código personalizado para combinar las directivas:

- Establecer **aceptación personalizada usa** para agregar su propio código para determinar si una instancia determinada del elemento de Index Server se debe combinar en el elemento de destino. Cuando el usuario arrastra desde el cuadro de herramientas, se muestra el puntero "no válido" si el código no permite la combinación.

   Por ejemplo, podría permitir la fusión mediante combinación solo cuando el elemento receptor está en un estado determinado.

- Establecer **combinación personalizada usa** para agregar proporcionan el propio código para definir los cambios realizados en el modelo cuando se realiza la combinación.

   Por ejemplo, podría establecer propiedades en el elemento combinado mediante el uso de datos desde su nueva ubicación en el modelo.

> [!NOTE]
> Si escribe código personalizado de mezcla, afecta sola combinaciones que se realizan mediante el uso de este EMD. Si hay otros EMDs que combinación el mismo tipo de objeto, o si hay otro código personalizado que crea estos objetos sin utilizar el EMD, a continuación, no afectará el código personalizado de mezcla.
>
> Si desea asegurarse de que un nuevo elemento o una nueva relación siempre se procesa el código personalizado, considere la posibilidad de definir un `AddRule` en la relación de incrustación y un `DeleteRule` en la clase de dominio del elemento. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Ejemplo: Definir una EMD sin código personalizado

En el siguiente ejemplo permite a los usuarios crear un elemento y un conector al mismo tiempo, arrastre desde el cuadro de herramientas a una forma existente. El ejemplo agrega una EMD a la definición de DSL. Antes de esta modificación, los usuarios pueden arrastrar herramientas al diagrama, pero no en formas existentes.

Los usuarios también pueden pegar elementos en otros elementos.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Para permitir que los usuarios crear un elemento y un conector al mismo tiempo

1. Crear un DSL nuevo mediante el **lenguaje mínimo** plantilla de solución.

    Al ejecutar este DSL, le permite crear formas y conectores entre las formas. No se puede arrastrar una nueva **ExampleElement** forma desde el cuadro de herramientas a una forma existente.

2. Para permitir que los usuarios combinar elementos en `ExampleElement` formas, crear un nuevo EMD en el `ExampleElement` la clase de dominio:

   1.  En **DSL Explorer**, expanda **clases de dominio**. Haga clic en `ExampleElement` y, a continuación, haga clic en **Agregar directiva de fusión de nuevo elemento**.

   2.  Asegúrese de que el **detalles de DSL** ventana está abierta, para que puedan ver los detalles de la nueva EMD. (Menú: **Ver**, **otros Windows**, **detalles de DSL**.)

3. Establecer el **clase de indexación** en la ventana Detalles de DSL, para definir qué clase de elementos se puede combinar en `ExampleElement` objetos.

    En este ejemplo, seleccione `ExampleElements`, de modo que el usuario puede arrastrar elementos nuevos a los elementos existentes.

    Tenga en cuenta que la clase de indización se convierte en el nombre de la EMD en el Explorador de DSL.

4. En **mezcla de proceso mediante la creación de vínculos**, agregue dos rutas de acceso:

   - Una ruta de acceso vincula el nuevo elemento con el modelo primario. La expresión de ruta de acceso que tiene que introducir navega desde el elemento existente, seguridad a través de la relación de incrustación para el modelo primario. Por último, especifica el rol en el nuevo vínculo a la que se asignará el nuevo elemento. La ruta de acceso es como sigue:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - La ruta de acceso de otro vincula el nuevo elemento a elemento existente. La expresión de ruta de acceso especifica la relación de referencia y el rol al que se le asignará el nuevo elemento. Esta ruta de acceso es como sigue:

      `ExampleElementReferencesTargets.Sources`

      Puede usar la herramienta de exploración de la ruta de acceso para crear cada ruta de acceso:

      1. En **mezcla de proceso mediante la creación de vínculos en rutas de acceso**, haga clic en  **\<Agregar ruta de acceso >**.

      2. Haga clic en la flecha desplegable a la derecha del elemento de lista. Aparece una vista de árbol.

      3. Expanda los nodos de árbol para formar la ruta de acceso que desee especificar.

5. Probar el DSL:

   1.  Presione **F5** para volver a generar y ejecutar la solución.

        Volver a generar tardará más tiempo del habitual porque se actualizará el código generado desde plantillas de texto para ajustarse a la nueva definición de DSL.

   2.  Cuando se ha iniciado la instancia experimental de Visual Studio, abra un archivo de modelo de su DSL. Cree algunos elementos de ejemplo.

   3.  Arrastre desde el **ejemplo elemento** herramienta en una forma existente.

        Aparece una forma nueva y esté vinculado a la forma con un conector existente.

   4.  Copie una forma existente. Seleccione otra forma y pegar.

        Se crea una copia de la primera forma.  Tiene un nombre nuevo y esté vinculado a la segunda forma con un conector.

Tenga en cuenta los siguientes puntos de este procedimiento:

-   Mediante la creación de directivas de combinación de elementos, puede permitir que cualquier clase de elemento para aceptar cualquier otro. Se crea el EMD en la clase de dominio receptora, y se especifica la clase de dominio aceptado en el **Index (clase)** campo.

-   Al definir las rutas de acceso, puede especificar los vínculos que deben usarse para conectar el nuevo elemento con el modelo existente.

     Los vínculos que especifique deben incluir una relación de incrustación.

-   El EMD afecta a ambas creación desde el cuadro de herramientas y también las operaciones de pegar.

     Si escribe código personalizado que crea nuevos elementos, puede invocar explícitamente el EMD utilizando el `ElementOperations.Merge` método. Esto garantiza que el código vincula nuevos elementos en el modelo en la misma manera que otras operaciones. Para obtener más información, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Ejemplo: Agregar código de aceptación personalizada a una EMD

Al agregar código personalizado a una EMD, puede definir el comportamiento de combinación más compleja. Este sencillo ejemplo impide que el usuario agregando más de un número fijo de elementos al diagrama. En el ejemplo se modifica el valor predeterminado EMD que acompaña a una relación de incrustación.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Escribir código de aceptación personalizada para restringir lo que puede agregar el usuario

1.  Crear un DSL con la **lenguaje mínimo** plantilla de solución. Abra el diagrama de definición de DSL.

2.  En el Explorador de DSL, expanda **clases de dominio**, `ExampleModel`, **directivas de combinación de elementos**. Seleccione la directiva de combinación del elemento que se denomina `ExampleElement`.

     Este EMD controla cómo el usuario puede crear nuevos `ExampleElement` objetos en el modelo, por ejemplo, arrastre desde el cuadro de herramientas.

3.  En el **detalles de DSL** ventana, seleccione **aceptación personalizada usa**.

4.  Recompilar la solución. Esto tardará más tiempo del habitual porque el código generado se actualizará desde el modelo.

     Un error de compilación será notificado, al igual que: "Company.ElementMergeSample.ExampleElement no contiene una definición para CanMergeExampleElement..."

     Debe implementar el método `CanMergeExampleElement`.

5.  Cree un nuevo archivo de código en el **Dsl** proyecto. Reemplace su contenido por el código siguiente y cambiar el espacio de nombres al espacio de nombres del proyecto.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    Este sencillo ejemplo restringe el número de elementos que se pueden combinar en el modelo primario. Para condiciones más interesantes, puede inspeccionar el método cualquiera de las propiedades y los vínculos del objeto receptor. También puede inspeccionar las propiedades de los elementos de combinación, que se realizan en un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Para obtener más información acerca de `ElementGroupPrototypes`, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md). Para obtener más información sobre cómo escribir código que lee un modelo, vea [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

6.  Probar el DSL:

    1.  Presione **F5** para recompilar la solución. Cuando se abre la instancia experimental de Visual Studio, abra una instancia de su DSL.

    2.  Crear nuevos elementos de varias maneras:

        - Arrastre desde el **ejemplo elemento** herramienta al diagrama.

        - En el **Explorador de modelos de ejemplo**, haga clic en el nodo raíz y, a continuación, haga clic en **Agregar nuevo elemento de ejemplo**.

        - Copiar y pegar un elemento en el diagrama.

    3.  Compruebe que no se puede usar cualquiera de estas formas de agregar más de cuatro elementos al modelo. Esto es porque todos usan la directiva de fusión de elemento.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Ejemplo: Agregar código personalizado de mezcla para una EMD

En el código de combinación personalizada, puede definir lo que sucede cuando el usuario arrastra una herramienta o pega en un elemento. Hay dos maneras de definir una combinación personalizada:

1. Establecer **usa mezcla personalizada** y proporcionar el código necesario. El código reemplaza el código generado de mezcla. Use esta opción si desea redefinir completamente lo que hace la combinación.

2. Invalidar el `MergeRelate` método y opcionalmente el `MergeDisconnect` método. Para ello, debe establecer el **genera doble derivada** propiedad de la clase de dominio. El código puede llamar el código generado de mezcla en la clase base. Use esta opción si desea realizar operaciones adicionales después de haber realizado la fusión mediante combinación.

   Estos métodos sólo afectan a las combinaciones que se realizan mediante el uso de este EMD. Si desea que afecte a todas las formas en que se puede crear el elemento combinado, una alternativa consiste en definir un `AddRule` en la relación de incrustación y un `DeleteRule` en la clase de dominio combinada. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Para invalidar MergeRelate

1.  En la definición de DSL, asegúrese de que ha definido el EMD a la que desea agregar el código. Si lo desea, puede agregar rutas de acceso y definir código de aceptación personalizada tal como se describe en las secciones anteriores.

2.  En el diagrama DslDefinition, seleccione la clase receptora de la combinación. Normalmente es la clase en el extremo de origen de una relación de incrustación.

     Por ejemplo, en un DSL generado a partir de la solución de lenguaje mínimo, seleccione `ExampleModel`.

3.  En el **propiedades** ventana, establezca **genera doble derivada** a **true**.

4.  Recompilar la solución.

5.  Inspeccionar el contenido de **Dsl\Generated Files\DomainClasses.cs**. Buscar métodos denominados `MergeRelate` y examinar su contenido. Esto ayudará a escribir sus propias versiones.

6.  En un nuevo archivo de código, escribir una clase parcial para la clase receptora y reemplazar el `MergeRelate` método. No se olvide de llamar al método base. Por ejemplo:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>Escribir código personalizado de mezcla

1. En **Dsl\Generated Code\DomainClasses.cs**, inspeccionar los métodos denominados `MergeRelate`. Estos métodos crean vínculos entre un elemento nuevo y el modelo existente.

    Asimismo, inspeccione métodos denominados `MergeDisconnect`. Estos métodos desvinculación un elemento del modelo cuando se va a eliminar.

2. En **DSL Explorer**, seleccione o cree la directiva de fusión del elemento que desea personalizar. En el **detalles de DSL** ventana, establezca **usa mezcla personalizada**.

    Al establecer esta opción, el **proceso de mezcla** y **reenviar mezcla** se omiten las opciones. El código se usa en su lugar.

3. Recompilar la solución. Se tardará más de lo habitual porque se actualizarán los archivos de código generado desde el modelo.

    Aparecerán mensajes de error. Haga doble clic en los mensajes de error para ver las instrucciones que aparecen en el código generado. Estas instrucciones le pedirá que suministre los dos métodos, `MergeRelate` *YourDomainClass* y `MergeDisconnect` *YourDomainClass*

4. Escribir los métodos en una definición de clase parcial en un archivo de código independiente. Los ejemplos que se ha inspeccionado anteriormente deben sugerir lo que necesita.

   Código de la combinación personalizada no afectará a código que crea los objetos y relaciones directamente y no afectará a otros EMDs. Para asegurarse de que se implementen los cambios adicionales, independientemente de cómo se crea el elemento, considere la posibilidad de escribir un `AddRule` y un `DeleteRule` en su lugar. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Redirigir a una operación de combinación

Una directiva de combinación directa redirige el destino de una operación de combinación. Normalmente, el nuevo destino es el primario de incrustación del destino inicial.

Por ejemplo, en un DSL que se creó con la plantilla de diagrama de componentes, los puertos se incrustan en los componentes. Los puertos se muestran como formas pequeñas en el borde de una forma de componente. El usuario crea puertos, arrastre la herramienta de puerto a una forma de componente. Pero en ocasiones, el usuario arrastra erróneamente la herramienta de puerto a un puerto existente, en lugar del componente, y se produce un error en la operación. Se trata de un error habitual cuando hay varios puertos existentes. Para ayudar al usuario para evitar este inconveniente, puede permitir que los puertos que se puedan arrastrar un puerto existente, pero tienen la acción que se redirige al componente primario. La operación funciona como si el elemento de destino fuera del componente.

Puede crear una directiva de combinación hacia delante en la solución de modelo de componentes. Si compila y ejecuta la solución original, debería ver que los usuarios pueden arrastrar a cualquier número de **puerto de entrada** o **puerto de salida** elementos desde el **cuadro de herramientas** para un **Componente** elemento. Sin embargo, no podrán arrastrar un puerto un puerto existente. El puntero no se avisa que este cambio no está habilitado. Sin embargo, puede crear una directiva de combinación directa para que un puerto que esté involuntariamente pasados a una existente **puerto de entrada** se reenvía a la **componente** elemento.

### <a name="to-create-a-forward-merge-directive"></a>Para crear una directiva de combinación directa

1. Crear un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla de modelo de componentes.

2. Mostrar el **DSL Explorer** , abra DslDefinition.dsl.

3. En el **DSL Explorer**, expanda **clases de dominio**.

4. El **ComponentPort** la clase de dominio abstracta es la clase base de ambos **InPort** y **OutPort**. Haga clic en **ComponentPort** y, a continuación, haga clic en **Agregar directiva de fusión de nuevo elemento**.

    Un nuevo **directiva de fusión de elemento** nodo aparece en el **directivas de combinación de elementos** nodo.

5. Seleccione el **directiva de fusión de elemento** nodo y abra el **detalles de DSL** ventana.

6. En la lista de clase de indización, seleccione **ComponentPort**.

7. Seleccione **reenviar fusión mediante combinación a otra clase de dominio**.

8. En la lista de selección de ruta de acceso, expanda **ComponentPort**, expanda **ComponentHasPorts**y, a continuación, seleccione **componente**.

    La nueva ruta de acceso debe ser similar a ésta:

    **ComponentHasPorts.Component/!Component**

9. Guarde la solución y, a continuación, transformar las plantillas, haga clic en el botón situado en la **el Explorador de soluciones** barra de herramientas.

10. Compile y ejecute la solución. Aparece una nueva instancia de Visual Studio.

11. En **el Explorador de soluciones**, abra Sample.mydsl. El diagrama y el **ComponentLanguage herramientas** aparecen.

12. Arrastre un **puerto de entrada** desde el **cuadro de herramientas** a otro **puerto de entrada.** A continuación, arrastre un **OutputPort** a un **InputPort** y, a continuación, a otro **OutputPort**.

     No debería ver el puntero no está disponible, y debe ser capaz de colocar el nuevo **puerto de entrada** en uno existente. Seleccione la nueva **puerto de entrada** y arrastrarlo a otro punto de la **componente**.

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md)
- [Ejemplo de diagramas de circuitos DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)