---
title: Personalizar la creación y el movimiento de los elementos
description: Obtenga información sobre cómo permitir que un elemento se arrastre en otro, ya sea desde el cuadro de herramientas o en una operación de pegar o mover.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01867bf4c5d3e9c60ad4a2ba0ed76c45eca055c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935591"
---
# <a name="customizing-element-creation-and-movement"></a>Personalizar la creación y el movimiento de los elementos

Puede permitir que un elemento se arrastre en otro, ya sea desde el cuadro de herramientas o en una operación de pegar o mover. Los elementos que se han desconectado se pueden vincular a los elementos de destino mediante las relaciones que se especifiquen.

Una directiva de combinación de elementos (EMD) especifica lo que ocurre cuando un elemento de modelo se *combina* en otro elemento de modelo. Esto ocurre cuando:

- El usuario arrastra desde el cuadro de herramientas hasta el diagrama o una forma.

- El usuario crea un elemento mediante un menú Agregar en el explorador o una forma de compartimiento.

- El usuario mueve un elemento de una calle a otra.

- El usuario pega un elemento.

- El código del programa llama a la Directiva de combinación de elementos.

Aunque es posible que las operaciones de creación parezcan distintas de las operaciones de copia, realmente funcionan de la misma manera. Cuando se agrega un elemento, por ejemplo desde el cuadro de herramientas, se replica un prototipo de él. El prototipo se combina en el modelo de la misma manera que los elementos que se han copiado de otra parte del modelo.

La responsabilidad de un EMD es decidir cómo se debe combinar un objeto o un grupo de objetos en una ubicación determinada del modelo. En concreto, decide qué relaciones deben crearse para vincular el Grupo combinado al modelo. También puede personalizarlo para establecer las propiedades y crear objetos adicionales.

![Diagrama que muestra un y antes y después de examinar un árbol de elementos y sus relaciones de referencia cuando una E M D determina cómo se agrega un nuevo elemento.](../modeling/media/dsl-emd_merge.png)

Un EMD se genera automáticamente cuando se define una relación de incrustación. Este EMD predeterminado crea una instancia de la relación cuando los usuarios agregan nuevas instancias secundarias al elemento primario. Puede modificar estos EMDs predeterminados, por ejemplo, agregando código personalizado.

También puede agregar su propia EMDs en la definición de DSL para permitir que los usuarios arrastren o peguen diferentes combinaciones de clases combinadas y de recepción.

## <a name="defining-an-element-merge-directive"></a>Definir una directiva de combinación de elementos

Puede Agregar directivas de combinación de elementos a clases de dominio, relaciones de dominio, formas, conectores y diagramas. Puede agregarlos o encontrarlos en el explorador de DSL en la clase de dominio receptor. La clase receptora es la clase de dominio del elemento que ya está en el modelo y en la que se combinará el elemento nuevo o copiado.

![Captura de pantalla del explorador de DSL que muestra la adición de un E M D con ExampleElement seleccionado como clase de indexación y la opción se aplica a las subclases activada.](../modeling/media/dsl-emd_details.png)

La **clase de indización** es la clase de dominio de los elementos que se pueden combinar en los miembros de la clase receptora. Este EMD también combinará las instancias de subclases de la clase de indexación, a menos que establezca **se aplica a las subclases** a false.

Hay dos tipos de directivas de combinación:

- Una directiva **Process Merge** especifica las relaciones por las que se debe vincular el nuevo elemento al árbol.

- Una directiva de **combinación hacia delante** redirige el nuevo elemento a otro elemento receptor, normalmente un primario.

Puede agregar código personalizado a las directivas de combinación:

- Set **usa Accept personalizado** para agregar su propio código y determinar si una instancia determinada del elemento de indización debe combinarse en el elemento de destino. Cuando el usuario arrastra desde el cuadro de herramientas, el puntero "no válido" muestra si el código no permite la combinación.

   Por ejemplo, puede permitir la fusión mediante combinación solo cuando el elemento receptor está en un estado determinado.

- Set **usa combinación personalizada** para agregar proporcionar código propio para definir los cambios que se realizan en el modelo cuando se realiza la combinación.

   Por ejemplo, puede establecer propiedades en el elemento combinado utilizando los datos de su nueva ubicación en el modelo.

> [!NOTE]
> Si escribe código de combinación personalizado, solo afectará a las combinaciones realizadas mediante este EMD. Si hay otros EMDs que combinen el mismo tipo de objeto, o si hay otro código personalizado que cree estos objetos sin usar EMD, no se verán afectados por el código de combinación personalizado.
>
> Si desea asegurarse de que el código personalizado siempre procese un nuevo elemento o una nueva relación, considere la posibilidad de definir un `AddRule` en la relación de incrustación y `DeleteRule` en la clase de dominio del elemento. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Ejemplo: definir un EMD sin código personalizado

En el ejemplo siguiente se permite a los usuarios crear un elemento y un conector al mismo tiempo arrastrando desde el cuadro de herramientas hasta una forma existente. En el ejemplo se agrega un EMD a la definición de DSL. Antes de realizar esta modificación, los usuarios pueden arrastrar herramientas al diagrama, pero no a las formas existentes.

Los usuarios también pueden pegar elementos en otros elementos.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Para permitir que los usuarios creen un elemento y un conector al mismo tiempo

1. Cree un nuevo DSL con la plantilla de solución de **idioma mínima** .

    Al ejecutar este DSL, le permite crear formas y conectores entre las formas. No se puede arrastrar una nueva forma **ExampleElement** desde el cuadro de herramientas hasta una forma existente.

2. Para permitir que los usuarios combinen elementos en `ExampleElement` formas, cree un nuevo EMD en la `ExampleElement` clase de dominio:

   1. En el **Explorador de DSL**, expanda clases de **dominio**. Haga clic con el botón secundario `ExampleElement` y, a continuación, haga clic en **Agregar nuevo elemento Directiva de combinación**.

   2. Asegúrese de que la ventana **detalles de DSL** está abierta para que pueda ver los detalles del nuevo EMD. (Menú: **Ver**, **otras ventanas**, **detalles de DSL**).

3. Establezca la **clase de indexación** en la ventana detalles de DSL para definir la clase de elementos que se pueden combinar en los `ExampleElement` objetos.

    En este ejemplo, seleccione `ExampleElements` , para que el usuario pueda arrastrar nuevos elementos a los elementos existentes.

    Tenga en cuenta que la clase de indexación se convierte en el nombre de EMD en DSL Explorer.

4. En **procesar combinación mediante la creación de vínculos**, agregue dos rutas de acceso:

   - Una ruta de acceso vincula el nuevo elemento al modelo primario. La expresión de ruta de acceso que necesita escribir navega desde el elemento existente hasta la relación de incrustación con el modelo primario. Por último, especifica el rol en el nuevo vínculo al que se asignará el nuevo elemento. La ruta de acceso es la siguiente:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - La otra ruta de acceso vincula el nuevo elemento al elemento existente. La expresión de ruta de acceso especifica la relación de referencia y el rol al que se asignará el nuevo elemento. Esta ruta de acceso es la siguiente:

      `ExampleElementReferencesTargets.Sources`

      Puede usar la herramienta de navegación ruta de acceso para crear cada ruta de acceso:

      1. En **procesar combinación creando vínculos en rutas** de acceso, haga clic en **\<add path>** .

      2. Haga clic en la flecha desplegable situada a la derecha del elemento de lista. Aparece una vista de árbol.

      3. Expanda los nodos del árbol para formar la ruta de acceso que desea especificar.

5. Pruebe el DSL:

   1. Presione **F5** para volver a compilar y ejecutar la solución.

        La regeneración tardará más de lo habitual, ya que el código generado se actualizará desde las plantillas de texto para ajustarse a la nueva definición de DSL.

   2. Cuando se haya iniciado la instancia experimental de Visual Studio, abra un archivo de modelo de su DSL. Cree algunos elementos de ejemplo.

   3. Arrastre desde la herramienta **elemento de ejemplo** hasta una forma existente.

        Aparece una nueva forma y está vinculada a la forma existente con un conector.

   4. Copiar una forma existente. Seleccione otra forma y pegue.

        Se crea una copia de la primera forma.  Tiene un nuevo nombre y se vincula a la segunda forma con un conector.

Tenga en cuenta los siguientes puntos de este procedimiento:

- Mediante la creación de directivas de combinación de elementos, puede permitir que cualquier clase de elemento acepte cualquier otro. El EMD se crea en la clase de dominio receptor y la clase de dominio aceptada se especifica en el campo **clase de índice** .

- Al definir las rutas de acceso, puede especificar qué vínculos se deben usar para conectar el nuevo elemento al modelo existente.

     Los vínculos que especifique deben incluir una relación de incrustación.

- EMD afecta a la creación desde el cuadro de herramientas y también a las operaciones de pegado.

     Si escribe código personalizado que crea nuevos elementos, puede invocar explícitamente el EMD mediante el `ElementOperations.Merge` método. Esto garantiza que el código vincula nuevos elementos al modelo de la misma manera que otras operaciones. Para obtener más información, vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Ejemplo: agregar código de aceptación personalizado a un EMD

Al agregar código personalizado a un EMD, puede definir un comportamiento de combinación más complejo. En este sencillo ejemplo se evita que el usuario agregue más de un número fijo de elementos al diagrama. En el ejemplo se modifica el valor predeterminado de EMD que acompaña a una relación de incrustación.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Para escribir código de aceptación personalizado para restringir lo que el usuario puede Agregar

1. Cree un DSL con la plantilla de solución de **idioma mínimo** . Abra el diagrama de definición de DSL.

2. En DSL Explorer, expanda **clases de dominio**, `ExampleModel` , directivas de combinación de **elementos**. Seleccione la Directiva de combinación de elementos denominada `ExampleElement` .

     Este EMD controla cómo el usuario puede crear nuevos `ExampleElement` objetos en el modelo, por ejemplo arrastrando desde el cuadro de herramientas.

3. En la ventana **detalles de DSL** , seleccione **usa aceptación personalizada**.

4. Recompilar la solución. Esto tardará más de lo habitual, ya que el código generado se actualizará a partir del modelo.

     Se informará de un error de compilación similar a: "Company. ElementMergeSample. ExampleElement no contiene una definición para CanMergeExampleElement..."

     Debe implementar el método `CanMergeExampleElement` .

5. Cree un nuevo archivo de código en el proyecto **DSL** . Reemplace su contenido por el código siguiente y cambie el espacio de nombres al espacio de nombres del proyecto.

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

    En este sencillo ejemplo se restringe el número de elementos que se pueden combinar en el modelo primario. En el caso de condiciones más interesantes, el método puede inspeccionar cualquiera de las propiedades y los vínculos del objeto receptor. También puede inspeccionar las propiedades de los elementos de combinación, que se incluyen en <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Para obtener más información sobre `ElementGroupPrototypes` , vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md). Para obtener más información sobre cómo escribir código que lea un modelo, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. Pruebe el DSL:

    1. Presione **F5** para volver a compilar la solución. Cuando se abra la instancia experimental de Visual Studio, abra una instancia de su DSL.

    2. Cree nuevos elementos de varias maneras:

        - Arrastre desde la herramienta **elemento de ejemplo** hasta el diagrama.

        - En el **Explorador de modelos de ejemplo**, haga clic con el botón secundario en el nodo raíz y, a continuación, haga clic en **Agregar nuevo elemento de ejemplo**.

        - Copie y pegue un elemento en el diagrama.

    3. Compruebe que no puede usar ninguna de estas maneras para agregar más de cuatro elementos al modelo. Esto se debe a que todos utilizan la Directiva de combinación de elementos.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Ejemplo: agregar código de combinación personalizado a un EMD

En el código de combinación personalizado, puede definir lo que ocurre cuando el usuario arrastra una herramienta o la pega en un elemento. Hay dos maneras de definir una combinación personalizada:

1. Set **usa la combinación personalizada** y proporciona el código necesario. El código reemplaza el código de combinación generado. Utilice esta opción si desea volver a definir completamente lo que hace la combinación.

2. Invalide el `MergeRelate` método y, opcionalmente, el `MergeDisconnect` método. Para ello, debe establecer la propiedad **genera Double derived** de la clase de dominio. El código puede llamar al código de combinación generado en la clase base. Utilice esta opción si desea realizar operaciones adicionales después de que se haya realizado la combinación.

   Estos enfoques solo afectan a las combinaciones que se realizan mediante este EMD. Si desea influir en todas las formas en que se puede crear el elemento combinado, una alternativa consiste en definir un `AddRule` en la relación de incrustación y `DeleteRule` en la clase de dominio combinado. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Para invalidar MergeRelate

1. En la definición de DSL, asegúrese de que ha definido el EMD al que desea agregar el código. Si lo desea, puede agregar rutas de acceso y definir código de aceptación personalizado como se describe en las secciones anteriores.

2. En el diagrama DslDefinition, seleccione la clase receptora de la combinación. Normalmente, es la clase en el extremo de origen de una relación de incrustación.

     Por ejemplo, en un DSL generado a partir de la solución de idioma mínimo, seleccione `ExampleModel` .

3. En la ventana **propiedades** , establezca **genera Double derived** en **true**.

4. Recompilar la solución.

5. Inspeccione el contenido de **Dsl\Generated Files\DomainClasses.CS**. Busque métodos denominados `MergeRelate` y examine su contenido. Esto le ayudará a escribir sus propias versiones.

6. En un nuevo archivo de código, escriba una clase parcial para la clase receptora e invalide el `MergeRelate` método. Recuerde llamar al método base. Por ejemplo:

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

### <a name="to-write-custom-merge-code"></a>Para escribir código de combinación personalizado

1. En **Dsl\Generated Code\DomainClasses.CS**, inspeccione los métodos denominados `MergeRelate` . Estos métodos crean vínculos entre un nuevo elemento y el modelo existente.

    También puede inspeccionar métodos denominados `MergeDisconnect` . Estos métodos desvinculan un elemento del modelo cuando se va a eliminar.

2. En el **Explorador de DSL**, seleccione o cree la Directiva de combinación de elementos que desea personalizar. En la ventana **detalles de DSL** , establezca **usa combinación personalizada**.

    Cuando se establece esta opción, se omiten las opciones de **combinación de mezcla** y **reenvío** de proceso. En su lugar, se usa el código.

3. Recompilar la solución. Tardará más de lo habitual, ya que los archivos de código generado se actualizarán a partir del modelo.

    Aparecerán mensajes de error. Haga doble clic en los mensajes de error para ver las instrucciones en el código generado. Estas instrucciones le piden que suministre dos métodos, `MergeRelate` *YourDomainClass* y `MergeDisconnect` *YourDomainClass*

4. Escriba los métodos en una definición de clase parcial en un archivo de código independiente. Los ejemplos que inspeccionó anteriormente deberían sugerir lo que necesita.

   El código de combinación personalizado no afectará al código que crea objetos y relaciones directamente, y no afectará a otros EMDs. Para asegurarse de que se implementan los cambios adicionales con independencia de cómo se cree el elemento, considere la posibilidad de escribir un `AddRule` y un `DeleteRule` en su lugar. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Redirigir una operación Merge

Una directiva de combinación hacia delante redirige el destino de una operación de combinación. Normalmente, el nuevo destino es el elemento primario de inserción del destino inicial.

Por ejemplo, en un DSL que se creó con la plantilla de diagrama de componentes, los puertos se incrustan en los componentes. Los puertos se muestran como pequeñas formas en el borde de una forma de componente. El usuario crea puertos arrastrando la herramienta de puerto hasta una forma de componente. Pero a veces, el usuario arrastra erróneamente la herramienta de puerto a un puerto existente, en lugar del componente, y se produce un error en la operación. Este es un error sencillo cuando hay varios puertos existentes. Para ayudar al usuario a evitar esta molestia, puede permitir que los puertos se arrastren a un puerto existente, pero que la acción se redirija al componente primario. La operación funciona como si el elemento de destino fuera el componente.

Puede crear una directiva de combinación hacia delante en la solución modelo de componentes. Si compila y ejecuta la solución original, debería ver que los usuarios pueden arrastrar cualquier número de elementos de puerto de **entrada** o de **Puerto de salida** desde el **cuadro de herramientas** a un elemento de **componente** . Sin embargo, no pueden arrastrar un puerto a un puerto existente. El puntero no disponible le avisa de que este movimiento no está habilitado. Sin embargo, puede crear una directiva de combinación hacia delante para que un puerto que se coloque involuntariamente en un **Puerto de entrada** existente se reenvíe al elemento de **componente** .

### <a name="to-create-a-forward-merge-directive"></a>Para crear una directiva de combinación hacia delante

1. Cree una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla modelo de componentes.

2. Abra DslDefinition. DSL para mostrar el **Explorador de DSL** .

3. En el **Explorador de DSL**, expanda **clases de dominio**.

4. La clase de dominio Abstract **ComponentPort** es la clase base de **inport** y **Outport**. Haga clic con el botón secundario en **ComponentPort** y luego haga clic en **Agregar nuevo elemento Directiva de combinación**.

    Aparece un nuevo nodo de **Directiva de combinación de elementos** en el nodo directivas de combinación de **elementos** .

5. Seleccione el nodo de **Directiva de combinación de elementos** y abra la ventana de detalles de **DSL** .

6. En la lista clase de indexación, seleccione **ComponentPort**.

7. Seleccione **reenviar fusión mediante combinación a otra clase de dominio**.

8. En la lista selección de rutas de acceso, expanda **ComponentPort**, **ComponentHasPorts** y, a continuación, seleccione **componente**.

    La nueva ruta de acceso debe ser similar a esta:

    **Componente ComponentHasPorts. Component/!**

9. Guarde la solución y, a continuación, transforme las plantillas haciendo clic en el botón situado más a la derecha en la barra de herramientas **Explorador de soluciones** .

10. Compile y ejecute la solución. Aparecerá una nueva instancia de Visual Studio.

11. En **Explorador de soluciones**, abra sample. midsl. Aparecen el diagrama y el **cuadro de herramientas ComponentLanguage** .

12. Arrastre un **Puerto de entrada** desde el **cuadro de herramientas** a otro puerto de **entrada.** A continuación, arrastre **OutputPort** a **InputPort** y, a continuación, a otro **OutputPort**.

     No debe ver el puntero no disponible y debe poder quitar el nuevo **Puerto de entrada** en el existente. Seleccione el nuevo **Puerto de entrada** y arrástrelo hasta otro punto del **componente**.

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md)
- [Ejemplo de diagramas de circuitos DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
