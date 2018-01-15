---
title: "Personalizar la creación del elemento y movimiento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords: Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0310821ab2968f0709b002166d188a4ebc4c2ff4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-element-creation-and-movement"></a>Personalizar la creación y el movimiento de los elementos
Puede permitir que un elemento que se pueden arrastrar a otra, en el cuadro de herramientas o en una operación de pegado o la operación de movimiento. Puede tener los elementos movidos vinculados a los elementos de destino, mediante las relaciones que especifique.  
  
 Una directiva de mezcla element (EMD) especifica lo que ocurre cuando un elemento de modelo es *combinados* en otro elemento de modelo. Esto sucede cuando:  
  
-   El usuario arrastra desde el cuadro de herramientas hasta el diagrama o una forma.  
  
-   El usuario crea un elemento mediante el uso de un menú Agregar en el explorador o una forma de compartimiento.  
  
-   El usuario mueve un elemento de una calle a otra.  
  
-   El usuario pega un elemento.  
  
-   El código del programa llama a la directiva de mezcla de elemento.  
  
 Aunque las operaciones de creación pueden parecer sea distinto de las operaciones de copia, realmente funcionan de la misma manera. Cuando se agrega un elemento, por ejemplo en el cuadro de herramientas, un prototipo del mismo se replica. El prototipo se combina con el modelo de la misma manera como elementos que se han copiado desde otra parte del modelo.  
  
 La responsabilidad de un EMD consiste en decidir cómo se debe combinar un objeto o grupo de objetos en una ubicación determinada en el modelo. En concreto, decide qué relaciones se deberían crear instancias para vincular el grupo combinado en el modelo. También puede personalizar para establecer las propiedades y crear objetos adicionales.  
  
 ![DSL &#45; EMD &#95; Mezcla](../modeling/media/dsl-emd_merge.png "EMD_Merge DSL")  
El rol de una directiva de mezcla de elemento  
  
 Un EMD se genera automáticamente cuando se define una relación de incrustación. Este valor predeterminado EMD crea una instancia de la relación cuando los usuarios agreguen nuevas instancias de elemento secundario al elemento primario. Puede modificar estos EMDs de forma predeterminada, por ejemplo mediante la adición de código personalizado.  
  
 También puede agregar sus propios EMDs en la definición DSL, para permitir que los usuarios arrastrar o pegar diferentes combinaciones de clases combinadas y la recepción.  
  
## <a name="defining-an-element-merge-directive"></a>Definir una directiva de mezcla de elemento  
 Puede agregar directivas de mezcla de elemento para las clases de dominio, relaciones de dominio, formas, conectores y diagramas. Puede agregar o buscar en el Explorador de DSL en la clase de dominio receptora. La clase receptora es la clase de dominio del elemento que ya está en el modelo y en la que se van a combinar el elemento nuevo o copiar.  
  
 ![DSL &#45; EMD &#95; detalles](../modeling/media/dsl-emd_details.png "EMD_Details DSL")  
  
 El **indización clase** es la clase de dominio de los elementos que se pueden mezclar con los miembros de la clase receptora. Instancias de subclases de la clase de Index Server también se combinará por este EMD, a menos que establezca **se aplica a las subclases** en False.  
  
 Hay dos tipos de directiva de mezcla:  
  
-   A **proceso de mezcla** directiva especifica las relaciones por el que debe vincularse al nuevo elemento en el árbol.  
  
-   A **al día mezcla** directiva redirige el nuevo elemento a otro elemento de recepción, por lo general, un elemento primario.  
  
 Puede agregar código personalizado para combinar directivas:  
  
-   Establecer **Aceptar personalizado usa** para agregar su propio código para determinar si se debe combinar una instancia determinada del elemento de Index Server en el elemento de destino. Cuando el usuario arrastra desde el cuadro de herramientas, el puntero "no válido" en el que se muestra si el código no permite la combinación.  
  
     Por ejemplo, podría permitir la fusión mediante combinación solo cuando el elemento receptora está en un estado determinado.  
  
-   Establecer **mezcla personalizado usa** para agregar proporcionar código propio para definir los cambios realizados en el modelo cuando se realiza la combinación.  
  
     Por ejemplo, puede establecer propiedades en el elemento combinado mediante datos de su nueva ubicación en el modelo.  
  
> [!NOTE]
>  Si escribe un código de combinación personalizada, afecta solo combinaciones que se realizan usando este EMD. Si hay otros EMDs que la combinación del mismo tipo de objeto, o si hay otro código personalizado que crea estos objetos sin utilizar el EMD, a continuación, no se verá afectado por el código personalizado de mezcla.  
>   
>  Si desea asegurarse de que un nuevo elemento o una nueva relación siempre es procesado por el código personalizado, considere la posibilidad de definir un `AddRule` en la relación de incrustación y un `DeleteRule` en la clase de dominio del elemento. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="example-defining-an-emd-without-custom-code"></a>Ejemplo: Definir un EMD sin código personalizado  
 En el ejemplo siguiente, se permite a los usuarios crear un elemento y un conector al mismo tiempo, arrastre desde el cuadro de herramientas en una forma existente. El ejemplo agrega un EMD a la definición DSL. Antes de esta modificación, los usuarios pueden arrastrar herramientas en el diagrama, pero no en las formas existentes.  
  
 Los usuarios también pueden pegar elementos en otros elementos.  
  
#### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Para permitir a los usuarios crear un elemento y un conector al mismo tiempo  
  
1.  Crear un nuevo DSL mediante la **lenguaje mínimo** plantilla de solución.  
  
     Cuando se ejecuta este DSL, permite crear formas y conectores entre las formas. No se puede arrastrar un nuevo **ExampleElement** forma del cuadro de herramientas en una forma existente.  
  
2.  Para permitir que los usuarios de combinar elementos en `ExampleElement` formas, cree un nuevo EMD en la `ExampleElement` clase de dominio:  
  
    1.  En **DSL explorador**, expanda **clases de dominio**. Haga clic en `ExampleElement` y, a continuación, haga clic en **Agregar nuevo elemento mezcla directiva**.  
  
    2.  Asegúrese de que el **detalles de DSL** ventana está abierta, para que puedan ver los detalles de la nueva EMD. (Menú: **vista**, **otras ventanas**, **detalles de DSL**.)  
  
3.  Establecer el **indización clase** en la ventana Detalles de DSL, para definir qué clase de elementos se puede mezclar en `ExampleElement` objetos.  
  
     En este ejemplo, seleccione `ExampleElements`, de modo que el usuario puede arrastrar elementos nuevos a los elementos existentes.  
  
     Tenga en cuenta que la clase de indización se convierte en el nombre de la EMD en el Explorador de DSL.  
  
4.  En **mezcla de proceso mediante la creación de vínculos**, agregar dos rutas de acceso:  
  
    1.  Una ruta de acceso vincula el elemento nuevo al modelo primario. La expresión de ruta de acceso que tiene que introducir navega desde el elemento existente, una a través de la relación de incrustación para el modelo primario. Por último, especifica el rol en el nuevo vínculo a la que se asignará el nuevo elemento. La ruta de acceso es como sigue:  
  
         `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`  
  
    2.  La ruta de acceso de otro vincula el nuevo elemento al elemento existente. La expresión de ruta de acceso especifica la relación de referencia y el rol al que se asignará el nuevo elemento. Esta ruta de acceso es como sigue:  
  
         `ExampleElementReferencesTargets.Sources`  
  
     Puede usar la herramienta de exploración de la ruta de acceso para crear cada ruta de acceso:  
  
    1.  En **mezcla de proceso mediante la creación de vínculos en las rutas de acceso**, haga clic en  **\<Agregar ruta de acceso >**.  
  
    2.  Haga clic en la flecha de lista desplegable a la derecha del elemento de lista. Aparece una vista de árbol.  
  
    3.  Expanda los nodos en el árbol para formar la ruta de acceso que desea especificar.  
  
5.  Probar DSL:  
  
    1.  Presione F5 para volver a generar y ejecutar la solución.  
  
         Volver a generar tardará más tiempo de lo habitual porque el código generado se actualizarán desde plantillas de texto para que se ajuste a la nueva definición DSL.  
  
    2.  Cuando la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ha iniciado, abra un archivo de modelo del ADSL. Crear algunos elementos de ejemplo.  
  
    3.  Arrastre desde el **Example (elemento)** herramienta en una forma existente.  
  
         Aparece una nueva forma y se vincula a la forma con un conector existente.  
  
    4.  Copiar una forma existente. Seleccione otra forma y pegar.  
  
         Se crea una copia de la primera forma.  Tiene un nombre nuevo y se vincula a la segunda forma con un conector.  
  
 Tenga en cuenta los siguientes puntos de este procedimiento:  
  
-   Mediante la creación de directivas de mezcla de elemento, puede permitir que cualquier clase de elemento que se va a aceptar cualquier otro. El EMD se crea en la clase de dominio receptora, y se especifica la clase de dominio aceptado en el **Index (clase)** campo.  
  
-   Al definir las rutas de acceso, puede especificar los vínculos que deben utilizarse para conectar el nuevo elemento con el modelo existente.  
  
     Los vínculos que especifique deben incluir una relación de incrustación.  
  
-   El EMD afecta a ambas creación en el cuadro de herramientas y también las operaciones de pegar.  
  
     Si escribe código personalizado que crea nuevos elementos, puede invocar explícitamente el EMD mediante el `ElementOperations.Merge` método. Esto garantiza que el código vincula nuevos elementos en el modelo de la misma manera que otras operaciones. Para obtener más información, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).  
  
## <a name="example-adding-custom-accept-code-to-an-emd"></a>Ejemplo: Agregar código personalizado Aceptar a un EMD  
 Al agregar código personalizado a un EMD, puede definir el comportamiento de la combinación más complejo. Este sencillo ejemplo impide que el usuario agregar más de un número fijo de elementos al diagrama. En el ejemplo se modifica el valor predeterminado EMD que acompaña a una relación de incrustación.  
  
#### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Para escribir código personalizado acepta y restringir lo que puede agregar el usuario  
  
1.  Crear un DSL mediante la **lenguaje mínimo** plantilla de solución. Abra el diagrama de definición DSL.  
  
2.  En el Explorador de DSL, expanda **clases de dominio**, `ExampleModel`, **elemento Combinar directivas**. Seleccione la directiva de combinación del elemento que se denomina `ExampleElement`.  
  
     Este EMD controla cómo el usuario puede crear nuevos `ExampleElement` objetos en el modelo, por ejemplo, arrastre desde el cuadro de herramientas.  
  
3.  En el **detalles de DSL** ventana, seleccione **Aceptar personalizado usa**.  
  
4.  Recompilar la solución. Este proceso tardará más de lo habitual porque el código generado se actualizará desde el modelo.  
  
     Un error de compilación será notificado, al igual que: "Company.ElementMergeSample.ExampleElement no contiene una definición para CanMergeExampleElement..."  
  
     Debe implementar el método `CanMergeExampleElement`.  
  
5.  Crear un nuevo archivo de código en el **Dsl** proyecto. Reemplazar su contenido con el código siguiente y cambiar el espacio de nombres al espacio de nombres del proyecto.  
  
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
  
     Este sencillo ejemplo restringe el número de elementos que se pueden mezclar con el modelo primario. Condiciones de más interesante, el método puede inspeccionar cualquiera de las propiedades y los vínculos del objeto receptor. También pueden inspeccionar las propiedades de los elementos de combinación, que se realizan en un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Para obtener más información acerca de `ElementGroupPrototypes`, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md). Para obtener más información sobre cómo escribir código que lee un modelo, vea [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
6.  Probar DSL:  
  
    1.  Presione F5 para volver a generar la solución. Cuando la instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se abre, abra una instancia del ADSL.  
  
    2.  Crear nuevos elementos de varias maneras:  
  
        1.  Arrastre desde el **Example (elemento)** herramienta en el diagrama.  
  
        2.  En el **Explorador de modelos de ejemplo**, haga clic en el nodo raíz y, a continuación, haga clic en **Agregar nuevo elemento de ejemplo**.  
  
        3.  Copiar y pegar un elemento en el diagrama.  
  
    3.  Compruebe que no se puede utilizar cualquiera de estos métodos para agregar más de cuatro elementos al modelo. Esto es porque todas usan la directiva de mezcla de elemento.  
  
## <a name="example-adding-custom-merge-code-to-an-emd"></a>Ejemplo: Agregar código personalizado de mezcla a un EMD  
 En el código de combinación personalizada, puede definir lo que ocurre cuando el usuario arrastra una herramienta o lo pega en un elemento. Hay dos maneras de definir una combinación personalizada:  
  
1.  Establecer **usa mezcla personalizada** y proporcionar el código necesario. El código reemplaza el código generado de mezcla. Utilice esta opción si desea volver a definir completamente lo que hace la combinación.  
  
2.  Invalidar el `MergeRelate` (método) y, opcionalmente, el `MergeDisconnect` método. Para ello, debe establecer el **genera derivados dobles** propiedad de la clase de dominio. El código puede llamar el código generado de mezcla en la clase base. Utilice esta opción si desea realizar operaciones adicionales después de haber realizado la combinación.  
  
 Estos enfoques sólo afectan a combinaciones que se realizan usando este EMD. Si desea que afecte a todas las formas en el que se puede crear el elemento combinado, una alternativa consiste en definir una `AddRule` en la relación de incrustación y un `DeleteRule` en la clase de dominio combinada. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
#### <a name="to-override-mergerelate"></a>Para invalidar MergeRelate  
  
1.  En la definición DSL, asegúrese de que ha definido el EMD a la que desea agregar el código. Si lo desea, puede agregar rutas de acceso y definir personalizado acepta el código tal como se describe en las secciones anteriores.  
  
2.  En el diagrama DslDefinition, seleccione la clase de receptor de la combinación. Normalmente es la clase en el extremo de origen de una relación de incrustación.  
  
     Por ejemplo, en un DSL generado a partir de la solución de lenguaje mínima, seleccione `ExampleModel`.  
  
3.  En el **propiedades** ventana, establezca **genera derivados dobles** a **true**.  
  
4.  Recompilar la solución.  
  
5.  Inspeccionar el contenido de **Dsl\Generated Files\DomainClasses.cs**. Búsqueda de métodos denominados `MergeRelate` y examinar su contenido. Esto le ayudará a escribir sus propias versiones.  
  
6.  En un nuevo archivo de código, escribir una clase parcial para la clase de receptor y reemplazar el `MergeRelate` método. No olvide llamar al método base. Por ejemplo:  
  
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
  
#### <a name="to-write-custom-merge-code"></a>Escribir código personalizado de mezcla  
  
1.  En **Dsl\Generated Code\DomainClasses.cs**, inspeccionar los métodos denominados `MergeRelate`. Estos métodos crean vínculos entre un elemento nuevo y el modelo existente.  
  
     Asimismo, inspeccione métodos denominados `MergeDisconnect`. Estos métodos desvinculación un elemento del modelo una vez que va a eliminar.  
  
2.  En **DSL explorador**, seleccione o cree la directiva de mezcla de elemento que desea personalizar. En el **detalles de DSL** ventana, establezca **usa mezcla personalizada**.  
  
     Cuando se establece esta opción, el **proceso de mezcla** y **al día mezcla** opciones se omiten. El código se usa en su lugar.  
  
3.  Recompilar la solución. Tardará más de lo habitual porque los archivos de código generado se actualizará desde el modelo.  
  
     Aparecerán mensajes de error. Haga doble clic en los mensajes de error para ver las instrucciones que aparecen en el código generado. Estas instrucciones le preguntará si quiere proporcionar dos métodos, `MergeRelate` *YourDomainClass* y `MergeDisconnect` *YourDomainClass*  
  
4.  Escribir los métodos en una definición de clase parcial en un archivo de código independiente. Los ejemplos que anteriormente ha inspeccionado deberían proponer lo que necesita.  
  
 Código de combinación personalizada no tendrá ningún efecto código que crea objetos y relaciones directamente y no se verán afectadas otras EMDs. Para asegurarse de que los cambios adicionales se implementan sin tener en cuenta cómo se crea el elemento, considere la posibilidad de escribir un `AddRule` y `DeleteRule` en su lugar. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
## <a name="redirecting-a-merge-operation"></a>Redirigir una operación de combinación  
 Una directiva de combinación directa redirige el destino de una operación de combinación. Por lo general, el nuevo destino es el elemento primario de incrustación del destino inicial.  
  
 Por ejemplo, en DSL que se creó con la plantilla de diagrama de componentes, los puertos se incrustan en componentes. Se muestran los puertos como pequeñas formas en el borde de una forma de componente. El usuario crea puertos si arrastra una forma de componente en la herramienta de puerto. A veces, pero el usuario arrastra erróneamente la herramienta de puerto a un puerto existente, en lugar del componente, y se produce un error en la operación. Se trata de un error habitual cuando hay varios puertos existentes. Para ayudar al usuario para evitar esta molesto, puede permitir que los puertos que se pueden arrastrar a un puerto existente, pero tienen la acción que se redirige al componente primario. La operación funciona como si el elemento de destino fuera del componente.  
  
 Puede crear una directiva de mezcla hacia delante en la solución de modelo de componentes. Si se compila y ejecuta la solución original, debería ver que los usuarios pueden arrastrar cualquier número de **puerto de entrada** o **puerto de salida** elementos de la **cuadro de herramientas** para un **Componente** elemento. Sin embargo, no se arrastran un puerto a un puerto existente. Las alertas de puntero disponible que este movimiento no está habilitados. Sin embargo, puede crear una directiva de mezcla hacia delante para que un puerto que sea involuntariamente colocadas en una existente **puerto de entrada** se reenvía a la **componente** elemento.  
  
#### <a name="to-create-a-forward-merge-directive"></a>Para crear una directiva de mezcla hacia delante  
  
1.  Crear un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla de modelo de componentes.  
  
2.  Mostrar la **DSL explorador** abriendo DslDefinition.dsl.  
  
3.  En el **DSL explorador**, expanda **clases de dominio**.  
  
4.  El **ComponentPort** clase dominio abstracta es la clase base de ambos **InPort** y **OutPort**. Haga clic en **ComponentPort** y, a continuación, haga clic en **Agregar nuevo elemento mezcla directiva**.  
  
     Un nuevo **directiva de mezcla de Element** nodo aparece en el **elemento Combinar directivas** nodo.  
  
5.  Seleccione el **directiva de mezcla de Element** nodo y abra el **detalles de DSL** ventana.  
  
6.  En la lista de clases de indización, seleccione **ComponentPort**.  
  
7.  Seleccione **reenviar combinar en una clase de dominio diferente**.  
  
8.  En la lista de selección de la ruta de acceso, expanda **ComponentPort**, expanda **ComponentHasPorts**y, a continuación, seleccione **componente**.  
  
     La nueva ruta de acceso debe ser similar a este:  
  
     **ComponentHasPorts.Component/!Component**  
  
9. Guarde la solución y, a continuación, transformar las plantillas, haga clic en el botón situado en la **el Explorador de soluciones** barra de herramientas.  
  
10. Compile y ejecute la solución. Una nueva instancia de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aparece.  
  
11. En **el Explorador de soluciones**, abra Sample.mydsl. En el diagrama y la **ComponentLanguage herramientas** aparecen.  
  
12. Arrastre un **puerto de entrada** desde el **cuadro de herramientas** a otro **puerto de entrada.** A continuación, arrastre un **OutputPort** a una **InputPort** y, a continuación, a otro **OutputPort**.  
  
     No verá el puntero no está disponible, y debe poder colocar el nuevo **puerto de entrada** en una existente. Seleccione la nueva **puerto de entrada** y arrástrelo hasta otro punto el **componente**.  
  
## <a name="see-also"></a>Vea también  
 [Navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Personalizar las herramientas y el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md)   
 [Ejemplo de diagramas de circuito DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)